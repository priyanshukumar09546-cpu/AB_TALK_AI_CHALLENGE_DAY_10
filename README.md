# Day 10: Build Your First End-to-End Modular NLP Pipeline

**Challenge:** 60 Days AI Engineering Coding Challenge (`@ABTalksOnAI`)  
**Focus Area:** Pipeline Engineering  
**Tools:** Python, NLTK, Scikit-learn  

---

## 1. Overview
This project combines text preprocessing (Day 8) and TF-IDF vectorization with cosine similarity (Day 9) into a reusable, modular NLP pipeline. Raw text passes through independent, single-responsibility classes to produce ranked document similarity results with built-in edge-case validation.

---

## 2. Data-Flow Architecture Diagram

```text
+-------------------+       +------------------------+       +--------------------+
|   Raw Input Text  | ----> |  PreprocessingModule   | ----> |  Cleaned Tokens /  |
| (Query & Corpus)  |       | - Input Validation     |       |  Normalized Text   |
+-------------------+       | - Lowercase & Regex    |       +--------------------+
                            | - Stopword Removal     |                 |
                            | - Lemmatization        |                 v
                            +------------------------+       +--------------------+
                                                             |  VectorizerModule  |
+-------------------+       +------------------------+       | - fit(corpus)      |
|  Ranked Output    | <---- |     Pipeline Class     | <---- | - transform(query) |
| (Docs + Scores)   |       | - Orchestrates Flow    |       | - Cosine Similarity|
+-------------------+       | - Sorts by Similarity  |       +--------------------+
                            +------------------------+
