# StudyMeet AI

An AI-powered personalized learning platform that transforms your study materials into an interactive learning experience using Generative AI and Retrieval-Augmented Generation (RAG).

## Overview

StudyMeet AI is a full-stack learning platform where students can upload their study materials and use AI-powered tools to understand and practice their subjects.

Upload PDF, DOCX, PPTX, and TXT files to create a personal knowledge base and interact with your documents.

## Features

- Document Management: Upload and manage study materials.
- AI Tutor: Ask questions and get contextual answers from your documents.
- Smart Quiz: Generate MCQ-based quizzes with explanations and score calculation.
- AI Flashcards: Automatically generate flashcards from uploaded documents.
- Dashboard: Track documents, conversations, and learning activity.
- Authentication: Secure login and registration using JWT and bcrypt.
- RAG-based Search: Retrieve relevant document information using semantic search.

## Tech Stack

| Layer | Technologies |
|---|---|
| Frontend | React, Vite, Tailwind CSS |
| Backend | Node.js, Express.js |
| Database | MongoDB, Mongoose |
| AI / RAG | Python, FastAPI, LangChain |
| Embeddings | Sentence Transformers (MiniLM) |
| Vector Database | FAISS |
| LLM | GPT-OSS-20B via Hugging Face Inference Providers |
| Authentication | JWT, bcrypt |
| Tools | Git, GitHub, Axios |

## How RAG Works

StudyMeet AI uses Retrieval-Augmented Generation to provide answers based on uploaded study materials.

1. Document Upload – User uploads a document.
2. Text Extraction – Content is extracted from the file.
3. Text Chunking – Extracted text is divided into smaller chunks.
4. Embedding Generation – Chunks are converted into vector embeddings.
5. Vector Storage – Embeddings are stored using FAISS.
6. Semantic Search – Relevant chunks are retrieved for a user's question.
7. AI Generation – The retrieved context is used to generate an answer.

## System Architecture

```text
       React + Vite
            |
        REST API
            |
            v
      Node.js + Express
            |
       +----+-----+
       |          |
       v          v
    MongoDB   Python FastAPI
                   |
                RAG Service
                   |
             +-----+------+
             |            |
             v            v
           FAISS     Hugging Face
                     Inference API
```

## Project Structure

```text
StudyMeet-AI/
│
├── client/                 # React frontend
│   └── src/
│       ├── components/
│       ├── pages/
│       ├── services/
│       └── store/
│
├── server/                 # Node.js backend
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   └── services/
│
├── rag/                    # Python RAG service
│   ├── embeddings/
│   ├── loaders/
│   ├── services/
│   ├── vectorstore/
│   ├── main.py
│   └── requirements.txt
│
└── README.md
```

## Getting Started

### Prerequisites

- Node.js and npm
- Python 3.10+
- MongoDB
- Hugging Face access token with Inference Providers access

### 1. Clone the Repository

```bash
git clone https://github.com/pranavvv-git/StudyMeet-AI.git
cd StudyMeet-AI
```

### 2. Install Frontend Dependencies

```bash
cd client
npm install
```

Create `client/.env`:

```env
VITE_API_URL=http://localhost:5000/api
```

### 3. Install Backend Dependencies

```bash
cd ../server
npm install
```

Create `server/.env` and configure:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
RAG_URL=http://127.0.0.1:8000
```

### 4. Set Up the RAG Service

```bash
cd ../rag
python -m venv venv
```

Activate the environment on Windows:

```powershell
.\venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Create `rag/.env`:

```env
HF_TOKEN=your_huggingface_token
LLM_MODEL=openai/gpt-oss-20b
HF_PROVIDER=together
```

### 5. Run the Application

Start each service in a separate terminal.

**RAG Service:**

```bash
cd rag
uvicorn main:app --reload --port 8000
```

**Backend:**

```bash
cd server
npm run dev
```

**Frontend:**

```bash
cd client
npm run dev
```

Open the frontend URL displayed by Vite in your browser.

## API Overview

| Module | Endpoints |
|---|---|
| Authentication | `/api/auth/register`, `/api/auth/login`, `/api/auth/me` |
| Documents | `/api/documents/upload`, `/api/documents` |
| AI Tutor | `/api/chat` |
| Quizzes | `/api/quizzes/generate`, `/api/quizzes/submit` |
| Flashcards | `/api/flashcards/generate`, `/api/flashcards` |
| Dashboard | `/api/dashboard/stats` |

## Deployment

The application supports a multi-service deployment architecture:

- **Frontend:** Vercel or Render
- **Backend:** Render or Railway
- **Database:** MongoDB Atlas
- **RAG Service:** Render or another Python-compatible hosting platform

A Docker-based deployment option is also included for running the Node.js API and Python RAG service together.

Production deployments require properly configured environment variables and service URLs.

## What I Learned

- Full-stack application development
- REST API design and integration
- Authentication and authorization
- Document processing and file uploads
- Embeddings and vector search
- Retrieval-Augmented Generation
- LLM integration using Hugging Face
- Building and connecting multiple services

## Future Improvements

- Persistent cloud document storage
- Advanced learning analytics
- Personalized learning recommendations
- Spaced repetition for flashcards
- Streaming AI responses
- Background document processing

## Author

**Pranav Thakur**

Computer Science Engineering Student

Interests: Full-Stack Development, Backend Development, Generative AI and RAG Systems.

- GitHub: [pranavvv-git](https://github.com/pranavvv-git)

---

If you find this project interesting, consider giving it a ⭐ on GitHub.

License: Educational and portfolio purposes.
