# 📚 Retrieval-Augmented Generation (RAG) Pipeline

A Python-based **Retrieval-Augmented Generation (RAG)** project that retrieves relevant information from PDF documents using semantic search and generates context-aware answers with a Large Language Model (LLM).

The project combines document processing, text chunking, embedding generation, vector database storage, semantic retrieval, and LLM-based response generation.

## 🚀 Features

- **PDF Document Loading:** Load and process PDF files using LangChain document loaders.
- **Text Chunking:** Split documents into smaller chunks for efficient retrieval.
- **Text Embeddings:** Generate semantic embeddings using the `all-MiniLM-L6-v2` Sentence Transformer model.
- **Vector Database:** Store document chunks and embeddings in ChromaDB.
- **Semantic Search:** Retrieve relevant document chunks based on user queries.
- **LLM Integration:** Generate answers using the Groq API through LangChain.
- **Source Citations:** Display retrieved document sources and page information when available.
- **Streaming Responses:** Stream generated answers token by token or in chunks.
- **Answer Summarization:** Optionally summarize generated answers.
- **Query History:** Maintain a history of questions, answers, sources, and summaries.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| LangChain | Document processing and LLM integration |
| Sentence Transformers | Generate text embeddings |
| ChromaDB | Persistent vector storage |
| Groq API | LLM-powered answer generation |
| PyMuPDF | Extract text from PDF documents |
| python-dotenv | Manage environment variables |
| Jupyter Notebook | Development and experimentation |

## 📂 Project Structure

```text
RAG/
│
├── data/
│   ├── text_files/
│   │   ├── pdf/
│   │   │   ├── pdf1.pdf
│   │   │   ├── pdf2.pdf
│   │   │   └── pdf3.pdf
│   │   ├── machine_learning.txt
│   │   └── python.intro.txt
│   │
│   └── vector_store/          # Persistent ChromaDB data
│
├── notebook/
│   └── document.ipynb         # RAG implementation
│
├── .env                       # API key (do not upload)
├── .gitignore
├── requirements.txt
└── README.md
```

*The folder structure above represents the intended project layout. Your actual files may differ slightly.*

## ⚙️ Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

Replace the URL with your GitHub repository URL.

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Configure the Groq API key

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key_here
```

Get an API key from the [Groq Console](https://console.groq.com/keys).

Load the environment variable in Python:

```python
import os
from dotenv import load_dotenv

load_dotenv()

groq_api_key = os.getenv("GROQ_API_KEY")
```

**Security:** Never upload your `.env` file, API keys, or other secrets to GitHub.

### 5. Launch the notebook

Open the project in Visual Studio Code, select the virtual environment as your Jupyter kernel, and open:

```text
notebook/document.ipynb
```

Run the notebook cells in order, from imports and document loading through embedding generation, vector storage, retrieval, and answer generation.

## 🔄 How It Works

```text
PDF Documents
      |
      v
Document Loading
      |
      v
Text Chunking
      |
      v
Embedding Generation
      |
      v
ChromaDB Vector Store
      |
      v
User Question
      |
      v
Semantic Retrieval
      |
      v
Relevant Context + Question
      |
      v
Groq LLM
      |
      v
Generated Answer + Sources
      |
      v
Optional Summary + Query History
```

## 💻 Example Usage

The following example illustrates how the advanced pipeline can be called after the retriever and LLM have been initialized in the notebook:

```python
adv_rag = AdvancedRAGPipeline(rag_retriever, llm)

result = adv_rag.query(
    "SATELLITE BRIGHTNESS AND BLOCKAGE OF THE SKY",
    top_k=3,
    min_score=0.1,
    stream=True,
    summarize=True
)

print("Answer:", result["answer"])
print("Summary:", result["summary"])
print("Sources:", result["sources"])
```

### Query Parameters

| Parameter | Description |
|---|---|
| `question` | The user's question |
| `top_k` | Maximum number of relevant results to retrieve |
| `min_score` | Minimum similarity threshold, according to the retriever's scoring implementation |
| `stream` | Enables streamed LLM output |
| `summarize` | Enables optional answer summarization |

The retriever must implement the expected `retrieve()` interface and return document content, metadata, and similarity scores for this example to work.

## 📊 Example Output

A successful query may return:

- A generated answer based on retrieved context
- Retrieved document names and page information, where available
- Similarity scores for retrieved documents
- An optional two-sentence summary
- The latest query and answer in the conversation history

Actual results depend on the documents, retrieval settings, model, and API availability.

## 🔐 Environment Variables

| Variable | Description |
|---|---|
| `GROQ_API_KEY` | API key used to access the Groq LLM service |

Keep all API credentials private and use environment variables instead of hardcoding secrets.

## 🔮 Future Improvements

- Add a user-friendly web interface using Streamlit or Flask.
- Support Word documents and text files in addition to PDFs.
- Improve retrieval with hybrid search and reranking.
- Add persistent conversation history.
- Improve citation accuracy by linking individual claims to source passages.
- Add automated tests and error handling.
- Package the application for easier deployment.

## 📌 Learning Outcomes

This project demonstrates practical experience with:

- Retrieval-Augmented Generation architecture
- Document ingestion and preprocessing
- Semantic embeddings and vector databases
- Similarity-based information retrieval
- LLM integration using APIs
- Prompt engineering and context management
- Streaming responses, citations, and summarization
- Python development and environment configuration

## 👩‍💻 Author

**Visakha Thakur**

Computer Science and Engineering

---

*Built as a hands-on project to explore document-based question answering using Retrieval-Augmented Generation.*
