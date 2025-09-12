# Hybrid RAG (Dense + Sparse) Pipeline for Heart Disease Prevention Knowledge

<img width="2227" height="1137" alt="NotebookLM Mind Map" src="https://github.com/user-attachments/assets/0588385c-f473-43a4-9b5f-75c03e7506c7" />

## Overview

This repo demonstrates a Retrieval-Augmented Generation (RAG) pipeline that combines both dense (semantic) and sparse (keyword-based) search to answer questions about healthy eating for heart disease prevention. The pipeline is designed to ingest health-related textual data and generate informative, evidence-based answers using large language models (LLMs).

## What is Hybrid RAG?

- **Dense Retrieval:** Utilizes sentence embedding models, specifically transformer-based architectures, to create semantic representations of text chunks. This enables the system to retrieve information relevant to the meaning of the query, even when keywords do not match exactly.
- **Sparse Retrieval:** Employs traditional keyword-based statistical models such as TF-IDF (Term Frequency-Inverse Document Frequency) to identify chunks that contain query-specific words.
- **Reciprocal Rank Fusion (RRF):** Combines the results from both dense and sparse retrieval methods, ensuring that the most relevant and diverse information is surfaced for each query.

## Models and Vector DB Used

- **Dense (Semantic) Model:** The pipeline uses a sentence embedding model based on the transformer architecture (e.g., `sentence-transformers/all-MiniLM-L6-v2`). These models are designed to understand the semantic relationships between sentences, enabling effective vector-based search.
- **Sparse (Keyword) Model:** For keyword-based matching, the pipeline relies on (`TF-IDF`), a classic statistical text representation model that highlights the importance of terms within documents relative to a corpus.
- **Large Language Model (LLM):** The answer generation step utilizes a generative language model hosted on the Groq platform (e.g., `gpt/gpt-oss-20b`). These models synthesize coherent, context-aware answers based on the retrieved content.
- **Vector Database:** `Chroma DB` is used to store and manage the dense embeddings. It enables efficient similarity search and retrieval for semantic queries.

## Pipeline Steps

1. **Library Installation:** The pipeline leverages leading open-source libraries for natural language processing, retrieval, and vector search.
2. **Data Ingestion:** Health and nutrition content is loaded from a well-structured document focused on heart disease prevention.
3. **Text Chunking:** The document is split into manageable chunks, ensuring both context preservation and efficient retrieval.
4. **Dense Indexing:** Each chunk is embedded using a state-of-the-art sentence transformer and stored in Chroma DB for semantic search.
5. **Sparse Indexing:** The same chunks are indexed using TF-IDF, enabling keyword-based retrieval.
6. **Hybrid Search:** For any user query, both semantic and keyword-based retrieval are performed. The results are fused using Reciprocal Rank Fusion to maximize the quality of the answers.
7. **Question Answering:** The most relevant chunks are presented as context to a large language model, which synthesizes an informative answer tailored to the user’s question.

## Features

- **Comprehensive Retrieval:** Ensures both semantic relevance and keyword coverage.
- **Evidence-Based Answers:** Generates answers grounded in the latest health guidelines and research.
- **Customizable Context:** Can be adapted to ingest other health topics or documents.

## Output Example

Given a query like "I want to eat better to prevent heart disease. What should I avoid?", the pipeline provides a clear, actionable table and tips on foods and habits to avoid, along with guidance for making heart-healthy changes.

<img width="1757" height="521" alt="Screenshot 2025-09-12 175445" src="https://github.com/user-attachments/assets/a5e57d68-c493-4a51-a9d5-96cfe2c19385" />

