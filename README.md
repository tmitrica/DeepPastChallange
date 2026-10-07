# DeepPastChallenge

A comparative study of ByT5 architectures (Small, Base, Large) for translating ancient Akkadian transliterations into modern English, developed for the Kaggle Deep Past Challenge.

## Overview
The objective of this project is the automatic translation of Akkadian transliterated texts. Since Akkadian transliteration relies heavily on special diacritics, Unicode subscripts, and fragmented words due to broken tablets, traditional subword tokenizers are inefficient. This solution leverages the ByT5 architecture, which operates at the byte level and eliminates out-of-vocabulary issues.

## Repository Contents
* **[TranslateAkkadian.ipynb](TranslateAkkadian.ipynb)**: The code implementation containing data preprocessing, model training strategies, and generation scripts.
* **[TranslateAkkadianProject.pdf](TranslateAkkadianProject.pdf)**: The full project report detailing the methodologies, hardware constraints management, and failure mode analysis.

## Key Findings & Performance
Three model capacities were evaluated to find the optimal balance for the limited dataset size:

| Model | Parameters | BLEU Score | Description |
| :--- | :--- | :--- | :--- |
| **ByT5-Small** | ~300M | 23.94 | Effectively captured repetitive administrative formulas but struggled with longer narrative texts. |
| **ByT5-Base** | ~580M | **29.71** | **Best performance.** Maintained the optimal balance between grammatical abstraction and context memory. |
| **ByT5-Large (Partial)** | ~1.2B | 26.78 | Training was halted at epoch 5 due to the 12-hour hardware limit on Kaggle. |
| **ByT5-Large (Fully)** | ~1.2B | 20.57 | Heavily overfitted on the small dataset, degrading into a rigid lookup dictionary that failed on unseen data. |

> **Note:** The BLEU scores presented above are taken from the official competition evaluating on the hidden test set. Running the evaluation locally on a validation split might yield different absolute averages, but the comparative performance trend between the models should remain the same.
