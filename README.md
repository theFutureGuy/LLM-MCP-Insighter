# LLM-Insight-Search

**Semantic Web Discovery using LLMs**

---

## 🧠 Motivation

Traditional web search often returns irrelevant results for complex queries.  
**LLM-Insight-Search** semantically understands user intent, finds accurate documents, filters noise, and stores valuable content using modular AI-driven components.

---

## 🏗️ Construction

The project follows a modular design for easy customization and extension. Core modules:

| Component             | Function                                           |
|----------------------|----------------------------------------------------|
| **Query Optimizer**   | Enhances queries using Hugging Face Transformers   |
| **Search Engine**     | Fetches URLs using Brave Search API                |
| **Extractor**         | Extracts structured text via Firecrawl             |
| **Classifier**        | Ranks relevance using OpenAI's GPT models          |
| **Database**          | Saves results using MongoDB                        |

All modules can be replaced with minimal changes in `App.py`.

---

## ⚙️ Procedure

### 1. 🔧 Installation

```bash
python -m venv venv
source venv/bin/activate   # or `venv\Scripts\activate` on Windows
pip install -r requirements.txt
```

### 2. 🔑 Setup API Keys

Create a `.env` file in the root directory:

```
BRAVE_SEARCH_API_KEY=<your_key>
HF_API_KEY=<your_key>
FIRECRAWL_API_KEY=<your_key>
MONGO_DB_URI=<your_mongo_uri>
OPENAI_API_KEY=<your_key>
```

### 3. 🚀 Run the Application

```bash
python App.py
```

Follow on-screen prompts to complete the workflow.

---

## 🔁 Module API

Each module must expose specific functions:

### Query Optimization

```python
optimizer = HuggingFaceModule()
optimized_query = optimizer.optimize_query(user_query)
```

### Search Engine

```python
search_engine = BraveSearchEngine(result_count=10)
urls = search_engine.search(search_query)
```

### Text Extraction

```python
extractor = FirecrawlExtractor()
document, status_code = extractor.extract_text_from_url(url, level)
```

### Document Classification

```python
classifier = OpenAI()
relevance_result = classifier.classify_document(document["markdown"], search_query)
```

### MongoDB Integration

```python
db = MongoDB(database_name="default_db", collection_name="example_query")
db.show_database()
db.set_database("new_db")
db.set_collection("new_collection")
```

---

## 🔄 Module Replacement Guide

To replace any module:

1. **Update its initialization** in `App.py`.
2. **Keep function names consistent.**
3. **Ensure input/output types match original functions.**

This ensures seamless integration without breaking the system logic.
 
---
