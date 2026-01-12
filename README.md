#  HealthMate – AI Health Assistant Chatbot

HealthMate is a full-stack AI healthcare chatbot built using **Rasa** for natural language understanding and dialogue management, along with a modern **HTML/CSS/JavaScript** web interface.

> **Disclaimer:** HealthMate is for educational and demonstration purposes only. It does **not** provide medical diagnoses or professional medical advice.

---

##  Features

-  AI-powered chatbot using Rasa (NLU + Dialogue Management)
-  Web-based chat interface
-  Light / Dark theme toggle
-  Multi-language UI support (English / Hindi)
-  Real-time chat via REST API
-  Context-aware conversations using session IDs

---

## Project Architecture

```
Browser UI
   ↓  (HTTP REST)
Rasa Server (localhost:5005)
   ↓
Action Server (localhost:5055)
```

---

## Project Structure

```
healthmate-chatbot/
├── backend/
│   ├── actions/
│   ├── data/
│   ├── tests/
│   ├── config.yml
│   ├── domain.yml
│   ├── credentials.yml
│   ├── endpoints.yml
│   └── requirements.txt
│
├── ui/
│   └── public/
│       ├── index.html
│       └── chat.html
│
├── .gitignore
└── README.md
```

---

##  Tech Stack

- **Backend:** Python 3.10, Rasa 3.6
- **Frontend:** HTML, CSS, JavaScript
- **ML / NLP:** TensorFlow (via Rasa)
- **API:** Rasa REST Webhook
- **OS:** Linux (Arch Linux used during development)

---


System Architecture & Logic
------------------------------

Understanding how data flows through HealthMate is key to understanding its intelligence.

### 1\. The NLU Pipeline (The "Hearing" Brain)

When you type "I have a headache," Rasa's NLU (Natural Language Understanding) pipeline breaks it down:

*   **Intent Classification:** Identifying that the user is reporting a symptom (symptom\_report).
    
*   **Entity Extraction:** Picking out "headache" as the specific condition.
    

### 2\. Dialogue Management (The "Thinking" Brain)

Based on the stories.yml, the bot decides the next move. It doesn't just reply; it maintains **State**. If you say "It's been 2 days," the bot knows you are referring to the duration of the headache it just identified.

### 3\. The Action Server (The "Doing" Brain)

For complex logic (like checking a database or calculating a BMI), the Rasa server sends a request to the **Python Action Server**. This keeps the AI logic separate from the business logic.



## Key File Explanations
---------------------

To understand this project, look at these core files:

*   **domain.yml**: The "universe" of the bot—lists all intents, responses, and slots (memory).
    
*   **data/nlu.yml**: The training data that teaches the bot how to understand human language.
    
*   **config.yml**: Defines the ML policies (like DIETClassifier) used to train the model.



##  How to Run Locally

### 1- Clone the repository

```bash
git clone https://github.com/parthpant013-dot/healthmate-chatbot.git
cd healthmate-chatbot
```

---

### 2- Create virtual environment (Python 3.10 required)

```bash
python3.10 -m venv venv
source venv/bin/activate
pip install -r backend/requirements.txt
```

---

### 3- Train the chatbot model

```bash
cd backend
rasa train
```

---

### 4- Start backend servers

**Terminal 1 – Action Server**
```bash
rasa run actions
```

**Terminal 2 – Rasa Server**
```bash
rasa run --enable-api --cors "*"
```

---

### 5- Serve the frontend UI

```bash
cd ui/public
python -m http.server 8000
```

Open your browser and visit:
```
http://localhost:8000
```

---

## Testing

You can also test the chatbot directly in terminal:

```bash
cd backend
rasa shell
```

---

## Future Improvements

- Doctor appointment booking
- User authentication
- Persistent chat history
- Database integration
- Cloud deployment (Docker / AWS / GCP)

---


##  Developed by


**Parth**




























