# AI-Driven Phishing Email Detection Using NLP

An AI and Machine Learning project that detects phishing emails using Natural Language Processing (NLP), TF-IDF text features, and email metadata.

## Project Overview

Phishing emails are fraudulent messages designed to trick users into revealing sensitive information, clicking malicious links, or performing unsafe actions.

This project develops a machine learning-based phishing email detection system that analyzes email text and structural characteristics to classify emails as:

- Legitimate
- Phishing

The system applies NLP techniques for text classification and extracts metadata-based features such as URL information, email length, punctuation patterns, and sender-related information.

## Objectives

- Detect phishing emails automatically using Machine Learning.
- Apply Natural Language Processing to email text.
- Clean and preprocess email data.
- Extract meaningful linguistic and structural features.
- Convert email text into numerical features using TF-IDF.
- Extract metadata features from emails.
- Train and compare multiple Machine Learning models.
- Evaluate models using Accuracy, Precision, Recall, and F1-score.
- Analyze confusion matrices and feature importance.

## Dataset

The project uses the CEAS_08 phishing email dataset.

The dataset contains 39,154 email records with information such as:

- Sender
- Receiver
- Date
- Subject
- Body
- URLs
- Label

### Labels

| Label | Meaning |
|------:|---------|
| 0 | Legitimate |
| 1 | Phishing |

### Dataset Distribution

| Class | Number of Emails |
|---|---:|
| Legitimate | 17,312 |
| Phishing | 21,842 |
| Total | 39,154 |

## Project Workflow

Email Dataset  
↓  
Data Exploration  
↓  
Data Cleaning & Preprocessing  
↓  
Subject + Body Combination  
↓  
Text Cleaning  
↓  
Feature Engineering  
↓  
TF-IDF + Metadata Features  
↓  
Model Training  
↓  
Logistic Regression  
Random Forest  
Naive Bayes  
Neural Network  
↓  
Model Evaluation  
↓  
Accuracy, Precision, Recall, F1 Score  
↓  
Confusion Matrix & Feature Importance  
↓  
Final Analysis

## Data Preprocessing

The following preprocessing steps were performed:

1. Loaded the raw CEAS_08 dataset.
2. Handled missing values.
3. Combined email subject and body.
4. Converted text to lowercase.
5. Removed URLs.
6. Removed HTML tags.
7. Removed email addresses.
8. Removed punctuation.
9. Removed numerical values.
10. Removed extra whitespace.
11. Tokenized the text.
12. Removed English stopwords.
13. Removed empty cleaned emails.

## Feature Engineering

### TF-IDF

TF-IDF (Term Frequency-Inverse Document Frequency) was used to convert email text into numerical features.

Configuration:

- Maximum features: 10,000
- N-grams: Unigrams and bigrams
- Minimum document frequency: 2
- Maximum document frequency: 0.95
- English stopwords removed
- Sublinear TF enabled

The vectorizer was fitted only on the training data to avoid data leakage.

### Metadata Features

Additional structural features were extracted from the emails:

- URL count
- Presence of URL
- Subject length
- Body length
- Word count
- Exclamation mark count
- Question mark count
- Uppercase ratio
- Special character count
- Sender domain

These features help identify suspicious structural and linguistic patterns in phishing emails.

## Machine Learning Models

The following models were implemented and compared:

### Logistic Regression

A linear classification algorithm used for classifying emails based on TF-IDF text features.

### Naive Bayes

Multinomial Naive Bayes was used as a baseline model for text classification.

### Random Forest

Random Forest was used to capture non-linear relationships between features.

### Neural Network

A simple Multi-Layer Perceptron (MLP) with one hidden layer and ReLU activation was implemented.

## Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

### Results

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Logistic Regression | 99.46% | 99.43% | 99.61% | 99.52% |
| Random Forest | 98.94% | 99.22% | 98.88% | 99.05% |
| Neural Network | 97.85% | 98.01% | 98.15% | 98.08% |
| Naive Bayes | 96.36% | 99.83% | 93.64% | 96.63% |

## Best Performing Model

Logistic Regression achieved the best overall performance.

- Accuracy: 99.46%
- Precision: 99.43%
- Recall: 99.61%
- F1 Score: 99.52%

The high recall is particularly useful for phishing detection because it means the model successfully identifies most actual phishing emails.

Naive Bayes achieved the highest precision at 99.83%, but its recall was lower at 93.64%, meaning it missed more phishing emails compared with Logistic Regression.

## Evaluation Visualizations

The project includes visualizations for:

- Model accuracy comparison
- Accuracy, Precision, Recall and F1-score comparison
- Confusion matrices
- Important phishing-related features
- Random Forest feature importance
- Email metadata analysis

## Feature Importance

Logistic Regression coefficients were analyzed to identify features strongly associated with phishing emails.

Positive coefficients indicate features that push predictions toward the phishing class, while negative coefficients indicate features associated with legitimate emails.

Random Forest feature importance was also analyzed to identify influential features.

## Project Structure
```bash
phishing-email-detection-ml/
├── data/
│   ├── raw/
│   │   └── CEAS_08.csv
│   └── processed/
│       ├── cleaned_phishing_emails.csv
│       ├── tfidf_vectorizer.pkl
│       ├── X_train_tfidf.npz
│       ├── X_test_tfidf.npz
│       ├── X_train_metadata.csv
│       ├── X_test_metadata.csv
│       ├── y_train.csv
│       └── y_test.csv
│
├── models/
│   ├── logistic_regression.pkl
│   ├── naive_bayes.pkl
│   ├── random_forest.pkl
│   └── neural_network.pkl
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_model_training.ipynb
│   └── 05_evaluation.ipynb
│
├── results/
│   ├── model_comparison.csv
│   ├── evaluation_results.csv
│   ├── combined_feature_results.csv
│   └── top_phishing_features.csv
│
├── src/
├── .gitignore
└── README.md
```
## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- NLTK
- SciPy
- Matplotlib
- Jupyter Notebook
- Git & GitHub

## Key Concepts

This project demonstrates practical implementation of:

- Natural Language Processing
- Text Classification
- TF-IDF
- Feature Engineering
- Metadata Extraction
- Logistic Regression
- Naive Bayes
- Random Forest
- Neural Networks
- Model Evaluation
- Confusion Matrix
- Feature Importance
- Machine Learning for Cybersecurity

## Future Scope

The project can be extended by:

- Using larger and more diverse phishing email datasets.
- Applying Word2Vec or other word embeddings.
- Using advanced NLP models such as BERT.
- Adding more detailed URL and sender-domain analysis.
- Building a real-time phishing email detection application.
- Deploying the model using Flask or Streamlit.
- Adding Explainable AI techniques to show why an email was classified as phishing.

## Ethical Considerations

This project is intended for educational and cybersecurity research purposes.

The system should be used to improve email security and awareness. It should not be used to generate, distribute, or facilitate phishing attacks.

