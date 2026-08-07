# RAG Playground: A Collection of Retrieval-Augmented Generation Projects

Welcome to the **RAG Playground**! This repository is a central hub showcasing various Retrieval-Augmented Generation (RAG) implementations, custom search pipelines, and domain-specific search engines. 

Rather than a single tool, this repository serves as a portfolio of different RAG projects and experiments designed to query local documents and extract intelligent, context-aware information.

---

## 🌟 What is RAG? (The Core Concept)

If you ask a general AI a question about highly specialized information, personal files, or textbooks (like medical anatomy), it might hallucinate or fail to answer. 

**RAG (Retrieval-Augmented Generation)** solves this by connecting a smart search system to your AI. When you ask a question:
1. The system searches a local database of your documents.
2. It retrieves the most relevant paragraphs.
3. It hands those paragraphs to the AI as a reference sheet to generate a highly accurate, grounded answer.

---

## 📂 Featured Projects in this Repo

Below are the different RAG implementations included in this repository:

### 1. Base RAG Pipeline (`rag_pipeline.ipynb`)
* **Focus**: A modular, general-purpose document search pipeline.
* **How it works**:
  * **Loading**: Reads plain text (`.txt`) and PDF files (`.pdf`) using LangChain document loaders.
  * **Chunking**: Splits large documents into smaller, overlapping paragraphs.
  * **Embeddings**: Converts text blocks into 384-dimensional mathematical vectors using the `all-MiniLM-L6-v2` SentenceTransformer model.
  * **Database**: Indexes and saves embeddings locally in a **Chroma DB** vector store.
  * **Retrieval**: Performs fast semantic searches using cosine similarity to find documents closest in meaning to your query.

### 2. Anatomy Q&A RAG *(Coming Soon)*
* **Focus**: A specialized search pipeline optimized for medical and anatomy textbooks.
* **Details**: Custom processing rules for highly structured text, medical terminologies, and diagrams.

---

## 🛠️ The Common Workflow

All projects in this sandbox share this modular architecture:

```mermaid
graph TD
    A[Raw Documents: PDFs, TXT, Books] -->|Document Ingestion| B[Text Chunks]
    B -->|Embedding Model| C[Semantic Vectors]
    C -->|Store Ingested Data| D[(Local Vector DB - Chroma)]
    E[User Query] -->|Semantic Search| D
    D -->|Retrieve Matching Context| F[Context-Aware Prompt]
    F -->|Large Language Model| G[Grounded Answer]
    style D fill:#7b2cbf,stroke:#333,stroke-width:2px
```

---

## 🚀 Setup & Execution Guide

This repository uses **[uv](https://github.com/astral-sh/uv)** (an extremely fast Python package installer and resolver written in Rust) to manage packages and run notebooks.

### Prerequisites
Make sure you have **Python 3.8+** and **`uv`** installed. If you don't have `uv` installed, run:
```bash
# On Windows:
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"

# On macOS/Linux:
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### 1. Initialize Virtual Environment
Open your terminal in the repository directory and run:

```bash
# Create a virtual environment using uv
uv venv

# Activate the virtual environment
# On Windows:
.venv\Scripts\activate
# On macOS/Linux:
source .venv/bin/activate
```

### 2. Install Project Dependencies
Install the required packages at lightning speed using `uv`:

```bash
uv pip install -r requirements.txt
```

### 3. Run Notebooks
Launch Jupyter notebooks securely in the virtual environment:

```bash
uv run jupyter notebook
```
