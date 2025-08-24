# Space Facts RAG System

This project is a **Streamlit-based Retrieval-Augmented Generation (RAG)** application designed to answer questions about space using a curated set of facts. It integrates **ChromaDB** for vector storage, **OpenAI-compatible LLMs** via Ollama, and offers flexible embedding and language model options.

---

## Features

- User-friendly Streamlit UI for querying space-related facts
- Choice of LLMs: `llama3.1` or `llama3.2` via Ollama
- Choice of embedding models: `chroma` default or `nomic-embed-text` via Ollama
- Dynamic prompt augmentation using relevant fact retrieval
- Displays answer, references used, and augmented prompt

---

## Architecture Diagram

```mermaid
flowchart TD
   A[User (Streamlit UI)] -->|Query| B[RAG Pipeline]
   B --> C[ChromaDB (Vector Store)]
   B --> D[Prompt Augmentation]
   D --> E[LLM (Ollama llama3.1/3.2)]
   C --> B
   E --> F[Response]
   F --> A
   B --> G[References]
   G --> A
```


## Setup Instructions

> Ensure Ollama is running locally and supports `llama3.1`, `llama3.2`, and `nomic-embed-text` models.

### 2. Run the App

```bash
streamlit run app.py  # or whatever you name the file
```

---

## Included Space Facts

A static CSV file (`space_facts.csv`) is generated on the first run. It includes facts about:

- Human spaceflight (e.g., Yuri Gagarin)
- Moon landings
- Telescopes (Hubble, JWST)
- Mars exploration
- ISS, Voyager, SpaceX, black holes, etc.

---

## Models

### Embedding Models

| Option   | Description                                 |
| -------- | ------------------------------------------- |
| `chroma` | Chroma default embedding model (ONNXMiniLM) |
| `nomic`  | `nomic-embed-text` via Ollama API           |

### LLMs

| Option      | Description               |
| ----------- | ------------------------- |
| `ollama3.1` | llama3.1 model via Ollama |
| `ollama3.2` | llama3.2 model via Ollama |

---

## 🔎 RAG Workflow Summary

1. Load CSV facts and embed into ChromaDB
2. On user query:
   - Perform vector similarity search
   - Select top-k relevant facts
   - Construct prompt with context
   - Query LLM and show results

---

## Example Query

**User:** What is the Hubble Space Telescope?

**Context:** Retrieved facts mentioning Hubble

**LLM Response:** Explanation based on retrieved facts only

**References:** Facts used to answer

---

## File Structure

```
.
├── app.py                # Streamlit main application
├── space_facts.csv       # CSV of static facts (generated)
├── .env                  # API keys and settings
```

---

## Author

Jeffrey Gross

