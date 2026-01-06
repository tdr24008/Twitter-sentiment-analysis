# AI Bubble Discourse on X (Twitter)

This project analyses public discourse on X (formerly Twitter) to study whether users believe there is an “AI bubble”, whether they think it is about to burst, and what themes are associated with those beliefs. It uses weak supervision, classical NLP methods, and time-series aggregation to turn short social media posts into structured signals about belief, sentiment, and perceived risk.

The repository contains the raw data, the analysis notebook, and all code required to reproduce the results.

---

## Methods Used

The analysis pipeline consists of:

- **Data filtering & preprocessing**
  - English-only posts
  - Lowercasing, URL/user replacement, token normalisation, and stemming
- **Weak supervision for stance bootstrapping**
  - Keyword cues for `bubble` vs `not_bubble`
- **Stance classification**
  - TF–IDF (unigrams + bigrams) + Logistic Regression
- **Imminence detection**
  - Lexicon-based “burst imminence” score (burst + timing + hedge language)
- **Sentiment analysis**
  - VADER compound sentiment score
- **Topic modelling**
  - CountVectorizer + Latent Dirichlet Allocation (LDA)
- **Temporal aggregation**
  - Daily aggregation and 7-day rolling averages

---

## Reproducing the Results

### Option 1: Run in Google Colab (recommended)

1. Open `notebooks/X_platform_analysis.ipynb` in Google Colab.
2. Upload `data/x_bubble_raw.jsonl` when prompted (or mount Google Drive).
3. Run all cells from top to bottom.

All required libraries are installed inside the notebook.

## (Optional) Collecting New Data

If you want to regenerate the dataset, use `twitterapi.io` to query X and save results as a JSONL file with one post per line containing at least:

- `tweet_id`
- `created_at`
- `text`
- `lang`
