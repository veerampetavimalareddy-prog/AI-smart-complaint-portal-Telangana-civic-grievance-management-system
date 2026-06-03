# AI Smart Complaint Portal

A full-stack hackathon project for civic grievance management. Citizens can submit complaints, the backend classifies each complaint with an NLP-based AI service, and admins can view, filter, analyze, and update complaint status.

## Tech Stack

- **Frontend:** React.js, Vite, Tailwind CSS, Recharts
- **Backend:** FastAPI, SQLAlchemy
- **Database:** SQLite
- **AI:** Hugging Face Transformers zero-shot classification with keyword fallback

---

## Features

- Modern responsive landing page
- Complaint submission form
- Automatic complaint categorization:
  - Road Damage
  - Water Supply
  - Electricity
  - Garbage
  - Street Lights
  - Others
- Unique complaint ID generation
- Complaint tracking by ID
- Admin dashboard with filters and status updates
- Complaint count cards
- Category analytics chart
- Dark mode
- Mobile responsive layout

---

## Folder Structure

```text
project/
│
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   ├── components/
│   │   ├── services/
│   │   └── App.jsx
│
├── backend/
│   ├── main.py
│   ├── models.py
│   ├── database.py
│   ├── ai_classifier.py
│   ├── schemas.py
│   └── routes/
│
├── README.md
├── CONTRIBUTING.md
├── USER_MANUAL.md
└── AGENTS.md
```

---

## Backend Setup

### Prerequisites

- Python 3.10 or newer
- Node.js 18 or newer

### Create Virtual Environment

```bash
cd backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Optional AI Runtime

```bash
pip install -r requirements-ai.txt
```

### Run Backend Server

```bash
uvicorn main:app --reload
```

### Open API Docs

```text
http://localhost:8000/docs
```

SQLite database will be created automatically:

```text
backend/complaints.db
```

---

## Frontend Setup

### Install Dependencies

```bash
cd frontend
npm install
```

### Run Frontend

```bash
npm run dev
```

### Open Application

```text
http://localhost:5173
```

---

## API Endpoints

| Method | Endpoint | Description |
|----------|----------|-------------|
| POST | /complaint | Submit a new complaint |
| GET | /complaint/{id} | Track one complaint |
| GET | /complaints | List complaints with filters |
| PUT | /complaint/{id} | Update complaint status |
| GET | /stats | Get dashboard statistics |

---

## Example Complaint

### Input

```text
Street light is not working near my house
```

### Output Category

```text
Street Lights
```

---

## Notes

The AI classifier tries to load:

```text
facebook/bart-large-mnli
```

through Hugging Face Transformers when optional AI dependencies are installed.

If the model is unavailable, the application automatically falls back to the built-in keyword classifier, ensuring the demo remains fully functional without downloading large AI models.
