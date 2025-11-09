# 🤖 Emoji-Based Sentiment Analysis

## Project Overview

This repository contains the code and resources for **Activity 1: Emoji-Based Sentiment Analysis**, a machine learning project focused on classifying short text (tweets/posts) as either **POSITIVE** or **NEGATIVE**.

The core innovation of this project lies in its **robust feature engineering pipeline** designed to handle critical linguistic challenges, specifically **negation tagging** (e.g., converting "not good" to "good\_NEG") and **emoji utilization** (converting various emojis to a single `_EMOJI_` placeholder for effective model learning).

The final chosen model is **Logistic Regression ($\text{LR}$)**, which demonstrated the highest accuracy on the unseen test set after the feature pipeline was refined.

## 🚀 How to Run the Project

The primary output of this project is an interactive web application built with **Voila** that allows real-time sentiment analysis using the trained model.

### 1\. Prerequisites (Setup)

Ensure you have a Python environment (preferably a virtual environment like `.venv`) and the necessary packages installed.

```bash
# 1. Activate your virtual environment
# On macOS/Linux:
# source .venv/bin/activate
# On Windows (PowerShell):
.\.venv\Scripts\Activate.ps1

# 2. Install all required dependencies
pip install -r requirements.txt
# This includes pandas, scikit-learn, ipywidgets, and voila.
```

### 2\. Run the Interactive Analyzer

Once the dependencies are installed, you can launch the interactive sentiment analysis widget directly from the command line using **Voila**.

```bash
# Launch the notebook as a clean web application
voila CSS181-1_ACT1_GRP7.ipynb --strip_sources
```

This command will open a web browser tab displaying the interactive tool, where you can input text and see the model's prediction immediately.

## 📂 Repository Contents

| File Name | Description |
| :--- | :--- |
| `CSS181-1_ACT1_GRP7.ipynb` | **Main Project Notebook.** Contains the complete workflow: EDA, data cleaning, feature engineering, model training/evaluation for MNB, LR, and SVC, and the final interactive Voila widget code. |
| `1k_data_emoji_tweets_senti_posneg.csv` | **Raw Dataset.** The original input data used for training and testing. |
| `15_emoticon_data.csv` | **Emoji Reference Dataset.** Used to generate the custom regex pattern for emoji replacement. |
| `1k_data_emoji_tweets_SENTIMENT_CLEANED.csv` | **Final Cleaned Dataset.** The output of the fixed feature engineering pipeline, ready for model training. |
| `requirements.txt` | Lists all necessary Python package dependencies (e.g., `pandas`, `scikit-learn`, `nltk`, `ipywidgets`, `voila`). |
| `CSS181-1_ACT1_GRP7.html` | A static HTML export of the notebook. **Note:** Interactive widgets will not function in this file. |

## 💡 Key Feature Engineering

The project's success is attributed to its feature processing steps:

  * **Negation Tagging:** Critical negative words (e.g., "not") trigger a tag (`_NEG`) on the subsequent non-stopword to ensure the model correctly weights phrases like "I like the food" vs. "I do not like\_NEG the food."
  * **Emoji Tokenization:** All relevant emojis are converted into a single, standardized **`_EMOJI_`** token. This prevents the model from treating numerous rare emojis as separate features, thereby improving statistical significance and generalization.
