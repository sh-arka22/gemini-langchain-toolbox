# Gemini ✕ LangChain (Notebook)

A compact Jupyter/Colab notebook showing how to use **Google Gemini** models via both:
- the **`google-generativeai`** SDK (direct API usage), and
- **LangChain** (`langchain-google-genai`) for chaining, prompt templating, simple RAG, PAL (program-aided) math, and multimodal vision queries.

> Main artifact: **`Gemini_&_Langchain.ipynb`**

---

## What’s inside

The notebook walks through:

1. **Gemini SDK basics**
   - Configure API key
   - List available models
   - Generate text with `GenerativeModel(...).generate_content(...)`

2. **LangChain + Gemini (text chat)**
   - `ChatGoogleGenerativeAI`
   - Single-turn calls
   - Streaming token/chunk output

3. **LCEL chaining (Prompt → Model → Parser)**
   - `ChatPromptTemplate`
   - `StrOutputParser`
   - `prompt | model | parser`

4. **Mini RAG (in-memory)**
   - `GoogleGenerativeAIEmbeddings` (`models/embedding-001`)
   - `DocArrayInMemorySearch`
   - `RunnableMap` to assemble `{context, question}`

5. **PAL Chain**
   - `PALChain.from_math_prompt(...)` to solve math word problems via program-aided reasoning

6. **Multimodal (Vision)**
   - `gemini-pro-vision` with an image URL + a question in a single `HumanMessage`

---

## Requirements

- Python **3.10+** recommended
- Jupyter / Colab
- A **Google AI Studio / Gemini API key**

---

## Setup

### 1) Install dependencies

```bash
pip install -q langchain_experimental langchain_core
pip install -q google-generativeai==0.3.1 google-ai-generativelanguage
pip install -q langchain-google-genai
pip install -q "langchain[docarray]"
```

### 2) Set your API key

**macOS/Linux**
```bash
export GOOGLE_API_KEY="YOUR_KEY_HERE"
```

**Windows (PowerShell)**
```powershell
setx GOOGLE_API_KEY "YOUR_KEY_HERE"
```

> Never commit your API key to GitHub.

---

## Run

### Option A — Jupyter locally
```bash
jupyter lab
```
Open `Gemini_&_Langchain.ipynb` and run cells top-to-bottom.

### Option B — Google Colab
Upload the notebook to Colab and set `GOOGLE_API_KEY` in **Colab Secrets** or in the environment.

---

## Notes on model names

The notebook uses:
- `gemini-pro` (text)
- `gemini-pro-vision` (vision)
- `models/embedding-001` (embeddings)

If any of these are unavailable in your account/region, use the **“list models”** cell to pick a currently available alternative.

---

## Project structure

```text
.
├── Gemini_&_Langchain.ipynb
└── README.md
```

---

## Troubleshooting

- **Auth errors / 401**: confirm `GOOGLE_API_KEY` is set in the environment the notebook kernel is using.
- **Model not found**: run the model-listing cell and update the model string.
- **RAG returns weak answers**: add more/source texts, or swap in a persistent vector store.

---

## License

Add a license if you plan to publish this repo (MIT is a common default).
