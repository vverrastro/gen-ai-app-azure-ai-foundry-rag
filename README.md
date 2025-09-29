# Azure AI Foundry RAG Travel Assistant

This repository contains a **Retrieval-Augmented Generation (RAG) chat application** built with **Azure OpenAI** and **Azure Cognitive Search** as part of an Azure AI Foundry hands-on exercise. The app demonstrates how to integrate custom data into a generative AI solution for interactive, data-grounded responses.

---

## Overview

In this exercise, you will:

1. Create an **Azure AI Foundry hub and project**.
2. Deploy **embedding and chat models**.
3. Upload and index **custom data** (e.g., travel brochures).
4. Test your index in the **Playground**.
5. Build a **RAG client app** using the Azure OpenAI Python SDK.

**Note:** This exercise uses pre-release SDKs; some behaviors, warnings, or errors may occur. Users must have their Azure AI Foundry project, AI Search index, and model deployments already created.

---

## Features

* Interactive console-based chat.
* **RAG integration**: combines generative AI outputs with relevant information from custom data sources.
* Uses **Azure Cognitive Search** for vector-based retrieval.
* Maintains conversation history.
* Provides responses grounded in indexed data sources.

---

## Requirements

* Python 3.9+
* Dependencies in `requirements.txt`:

```bash
pip install -r requirements.txt
```

* A `.env` file with your Azure AI and Search configuration (see below).

---

## Configuration

The `.env` file should include:

```dotenv
OPEN_AI_ENDPOINT=<your Azure OpenAI endpoint>
OPEN_AI_KEY=<your Azure OpenAI API key>
CHAT_MODEL=<gpt-4o model deployment name>
EMBEDDING_MODEL=<text-embedding-ada-002 deployment name>
SEARCH_ENDPOINT=<Azure Cognitive Search endpoint>
SEARCH_KEY=<Azure Cognitive Search API key>
INDEX_NAME=<name of your search index>
```

> Ensure all Azure resources (OpenAI models, Search service, and index) are deployed and accessible.

---

## Usage

Run the chat app:

```bash
python rag-app.py
```

* Enter a question or prompt in the console.
* The assistant responds using both the **chat model** and **indexed data**.
* Type `quit` to exit the session.

**Example:**

```
Enter the prompt (or type 'quit' to exit): Where should I go on vacation to see architecture?
```

The response will include relevant data from your indexed brochures.

---

## How It Works

1. Loads environment variables from `.env`.
2. Initializes an **Azure OpenAI client**.
3. Maintains **chat history** with user and assistant messages.
4. Submits queries to **Azure Cognitive Search** using vector embeddings to retrieve relevant content.
5. Combines retrieved data with the chat prompt for **context-aware responses**.

---

## Included Files

* `rag-app.py` – Main RAG client application.
* `.env` – Configuration with keys and endpoints.
* `requirements.txt` – Python dependencies.

---

## Notes

* This exercise assumes you have already created:

  * An **Azure AI Foundry project and hub**.
  * **Embedding** and **chat model deployments**.
  * A **vector index** in **Azure Cognitive Search** populated with data.
* Responses are **grounded in your indexed data**, not just generic AI completions.

---

## Clean Up

To avoid unnecessary Azure costs:

1. Delete the **Azure AI Search** resource.
2. Delete the **Azure AI Foundry project resources** in your subscription.
