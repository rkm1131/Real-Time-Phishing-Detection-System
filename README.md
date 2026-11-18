# Real-Time Phishing Detection System

An ML-based phishing detection system designed to identify potentially malicious URLs using machine learning and provide users with real-time website safety checks through a web interface and Chrome browser extension.

## Overview

Phishing attacks use deceptive websites and URLs to trick users into revealing sensitive information such as login credentials and personal data.

This project implements a machine learning-based approach to phishing URL detection. It analyses URL-related features and predicts whether a given URL is legitimate or potentially phishing.

The system consists of three main components:

- **Frontend:** A web-based interface for submitting URLs and viewing prediction results.
- **Backend:** A FastAPI-based API that processes URL features and generates predictions using a trained machine learning model.
- **Chrome Extension:** A browser extension that helps users check URLs while browsing.

## Key Features

- Machine learning-based phishing URL classification.
- URL feature extraction and analysis.
- Integration of an XGBoost classification model.
- Web interface for URL submission and prediction results.
- REST API for communication between frontend and backend.
- Chrome extension for URL verification during browsing.
- Additional heuristic checks to support URL analysis.

## System Architecture

The system follows a modular architecture:

```text
                 User
                   |
          +--------+--------+
          |                 |
     Web Interface     Chrome Extension
          |                 |
          +--------+--------+
                   |
              FastAPI
               Backend
                   |
          URL Feature Extraction
                   |
           Heuristic Checks
                   |
          Trained ML Model
              (XGBoost)
                   |
          Prediction Result
                   |
          SAFE / PHISHING
```

## Machine Learning Approach

The machine learning component uses the **UCI Phishing Websites Dataset**.

### Dataset Information

- Original dataset size: 11,055 records.
- Total attributes: 31.
- Input features: 30.
- Target variable: 1.
- Duplicate records were removed during preprocessing, resulting in 5,849 records.

The dataset contains URL and website-related attributes used to distinguish legitimate websites from phishing websites.

### Models Evaluated

The following machine learning algorithms were evaluated:

1. Logistic Regression
2. Random Forest
3. XGBoost

After comparing their performance, XGBoost was selected as the final model.

### Model Performance

The selected XGBoost model achieved the following results on the evaluated test set:

| Metric | Score |
|---|---:|
| Accuracy | 95.13% |
| Precision | 95.04% |
| Recall | 94.88% |
| F1-Score | 94.96% |

These results indicate the model's performance on the evaluation dataset and do not guarantee the same accuracy on every real-world URL.

## Technology Stack

| Component | Technologies |
|---|---|
| Programming Language | Python, JavaScript |
| Machine Learning | XGBoost, Scikit-learn |
| Backend | FastAPI |
| Frontend | HTML, CSS, JavaScript |
| Browser Extension | Chrome Extension Manifest V3 |
| Model Storage | Joblib |
| API Communication | REST API |
| Dataset | UCI Phishing Websites Dataset |

## Repository Structure

```text
Real-Time-Phishing-Detection-System/
│
├── frontend/
│   ├── index.html
│   ├── script.js
│   └── style.css
│
├── backend/
│   ├── app/
│   │   ├── feature_extractor.py
│   │   ├── heuristic_checks.py
│   │   ├── main.py
│   │   ├── model_loader.py
│   │   └── predict.py
│   │
│   └── models/
│       ├── xgboost_phishing_model.joblib
│       └── phishing_scaler.joblib
│
└── chrome-extension/
    └── Extension source files
```

*Note: The structure above highlights the main components. Refer to the respective folders for the complete source files.*

## Live Deployment

The backend API is deployed on Render.

**API Base URL:**

https://phishing-detection-api-n362.onrender.com/

**Prediction Endpoint:**

`POST /predict`

The frontend communicates with the prediction API to submit URLs and display the resulting classification.

## Running the Project Locally

### 1. Clone the Repository

```bash
git clone https://github.com/rkm1131/Real-Time-Phishing-Detection-System.git

cd Real-Time-Phishing-Detection-System
```

### 2. Set Up the Backend

Navigate to the backend directory:

```bash
cd backend
```

Create and activate a Python virtual environment:

```bash
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Install the dependencies listed in the backend dependency file, if provided.

Start the FastAPI application using the project's configured Uvicorn entry point.

The local API is expected to be available at:

`http://127.0.0.1:8000`

### 3. Run the Frontend

Open the frontend directory and serve `index.html` using a local development server, such as the VS Code Live Server extension.

Ensure the frontend API configuration points to the running backend.

### 4. Load the Chrome Extension

1. Open Google Chrome.
2. Navigate to `chrome://extensions/`.
3. Enable **Developer mode**.
4. Click **Load unpacked**.
5. Select the `chrome-extension` folder.

The extension can then be used to check URLs while browsing.

## Future Enhancements

- Improve detection using larger and more diverse datasets.
- Explore additional machine learning and deep learning approaches.
- Enhance detection of newly emerging phishing techniques.
- Improve the user interface and browser extension experience.
- Expand real-time monitoring and reporting capabilities.

## Project Information

**Project Title:** Real-Time Phishing Detection System Using Machine Learning

**Project Type:** Major Academic Project

**Developer:** Rohit Kumar Mahato

**GitHub Repository:**  
https://github.com/rkm1131/Real-Time-Phishing-Detection-System

---

*This project was developed for academic and learning purposes. Predictions should be treated as an additional security layer and not as a replacement for standard cybersecurity practices.*
