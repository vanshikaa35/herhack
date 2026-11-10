# Sujh Bujh — AI-Powered Civic Problem Solving Platform

**Turning citizens' problems into actionable solutions through Artificial Intelligence.**

Sujh Bujh is an AI-powered civic innovation platform designed to bridge the gap between citizens reporting societal problems and institutions capable of solving them.

The platform allows citizens to report local problems in their own words. Using AI-powered analysis, it categorises complaints, detects potentially duplicate reports, identifies relevant institutions and recommends solutions based on existing research and successful implementations.

Our goal is to make civic problem-solving more organised, intelligent and collaborative.

---

## Problem Statement

Citizens frequently encounter problems related to water supply, sanitation, waste management, education, healthcare and public infrastructure.

However, these problems often remain unresolved because:

- Citizens do not know which institution is responsible for addressing their concerns.
- Similar complaints are reported repeatedly without being consolidated.
- Relevant research and existing solutions are difficult to discover.
- Institutions lack an organised way to identify and prioritise reported problems.

Sujh Bujh aims to address these challenges through an intelligent, AI-assisted civic problem-solving system.

## Our Solution

Sujh Bujh creates a structured connection between citizens, civic problems and institutions.

The platform follows an intelligent workflow:

1. **Problem Submission:** Citizens submit a description of their problem along with its location.
2. **AI-Powered Classification:** AI analyses the complaint and identifies its most relevant category.
3. **Duplicate Detection:** The system checks whether a similar problem has already been reported.
4. **Institution Routing:** The complaint is matched with a relevant college or institution based on its category, location and available expertise.
5. **Solution Recommendations:** Relevant research-backed solutions and implementation examples are suggested.
6. **Human Review:** Complaints with low AI confidence are flagged for manual review.
7. **Dashboard Monitoring:** Submitted complaints and their statuses can be monitored through a centralised dashboard.

## Key Features

### 1. AI-Powered Complaint Classification
- Analyses natural-language complaint descriptions.
- Supports English, Hindi, Hinglish and mixed-language inputs.
- Identifies the most relevant predefined problem category.
- Provides an AI-generated summary and confidence score.

### 2. Intelligent Duplicate Detection
- Identifies potentially similar complaints.
- Helps consolidate repeated reports.
- Tracks duplicate counts against original complaints.

### 3. Smart Institution Routing
- Matches complaints with relevant institutions.
- Considers problem categories, location and institutional expertise.
- Provides an explanation for the routing decision.

### 4. Research-Backed Solution Recommendations
- Identifies relevant existing solutions.
- Connects problems with implementation examples.
- Provides information about outcomes, implementers and sources.

### 5. Human-in-the-Loop Review
- Flags complaints with low AI classification confidence.
- Prevents uncertain classifications from being automatically routed.
- Maintains a separate under-review status.

### 6. Civic Dashboard
- Displays total submitted complaints.
- Tracks assigned, under-review and resolved problems.
- Provides category-wise statistics.
- Displays recent complaint submissions.

---

## Technology Stack

| Component | Technologies |
|---|---|
| Frontend | React.js, Vite |
| Styling | Tailwind CSS |
| Routing | React Router |
| Icons | Lucide React |
| Backend | Node.js, Express.js |
| AI Integration | NVIDIA API |
| AI Model | OpenAI GPT-OSS-20B (through NVIDIA API) |
| Data Storage | JSON-based file storage |
| API Communication | REST APIs |

## System Architecture

```text
             CITIZEN
                |
                v
       React.js Frontend
                |
                v
       Complaint Submission
                |
                v
       Node.js + Express API
                |
                v
       AI-Powered Analysis
          (NVIDIA API)
                |
                v
       Complaint Classification
                |
          +-----+------+
          |            |
          v            v
     Duplicate      Confidence
     Detection        Check
          |            |
          |       +----+----+
          |       |         |
          |       v         v
          |   Automatic   Human
          |    Routing    Review
          |       |
          |       v
          |  Institution
          |    Matching
          |       |
          |       v
          |  Solution
          | Recommendations
          |       |
          +---+---+
              |
              v
        JSON Data Storage
              |
              v
       Civic Dashboard
```

## Project Structure

```text
Jharkhand-main/
│
├── backend/
│   ├── config/
│   │   └── db.js
│   │
│   ├── controllers/
│   │   └── problemController.js
│   │
│   ├── data/
│   │   ├── colleges.json
│   │   ├── institutions.json
│   │   ├── links.json
│   │   ├── problems.json
│   │   ├── quantifiers.json
│   │   ├── researchproblems.json
│   │   └── solutions.json
│   │
│   ├── routes/
│   │   └── problemRoutes.js
│   │
│   ├── services/
│   │   ├── aiService.js
│   │   ├── duplicateService.js
│   │   └── routingService.js
│   │
│   ├── package.json
│   ├── server.js
│   └── .env
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   ├── data/
│   │   ├── pages/
│   │   │   ├── Landing.jsx
│   │   │   ├── Submit.jsx
│   │   │   ├── RoutingResult.jsx
│   │   │   └── Dashboard.jsx
│   │   │
│   │   ├── services/
│   │   │   └── aiRouter.js
│   │   │
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   │
│   ├── package.json
│   └── vite.config.js
│
└── README.md
```

## Installation & Setup

Follow these steps to run the project locally.

### Prerequisites

Make sure you have installed:

- Node.js (LTS version)
- npm
- Git
- NVIDIA API key

### 1. Clone the Repository

```bash
git clone <https://github.com/vanshikaa35/herhack.git>
```

Navigate into the project directory:

```bash
cd Jharkhand-main
```

### 2. Configure the Backend

Navigate to the backend directory:

```bash
cd backend
```

Install the dependencies:

```bash
npm install
```

Create a `.env` file inside the backend folder:

```env
NVIDIA_API_KEY=your_nvidia_api_key
PORT=5000
```

Get your NVIDIA API key from:

https://build.nvidia.com/

### 3. Start the Backend Server

Run:

```bash
npm run dev
```

The backend server will start at:

```text
http://localhost:5000
```

To verify that the backend is running, open:

```text
http://localhost:5000/
```

Expected response:

```json
{
  "message": "Jharkhand Civic Innovation API is running!"
}
```

### 4. Configure the Frontend

Open a second terminal and navigate to the frontend directory:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

### 5. Start the Frontend

Run:

```bash
npm run dev
```

The frontend will be available at:

```text
http://localhost:5173/
```

Open the URL in your browser to access Sujh Bujh.

**Note:** Keep both frontend and backend terminals running simultaneously. The NVIDIA API integration also requires a valid API key. The current backend AI service uses `curl.exe` to make API requests, so Windows with curl available is the supported setup for this version.

---

## 🔗 API Endpoints

The backend exposes REST API endpoints under `/api/problems`.

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/problems` | Submit and analyse a new complaint |
| GET | `/api/problems` | Retrieve all complaints |
| GET | `/api/problems/stats` | Retrieve complaint statistics |
| GET | `/api/problems/:id` | Retrieve a complaint by ID |
| PATCH | `/api/problems/:id/status` | Update complaint status |

### Example: Submit a Complaint

**POST** `/api/problems`

Request body:

```json
{
  "description": "There has been no water supply in our area for five days.",
  "location": "Ranchi, Ward 4"
}
```

The backend processes the complaint and returns its classification, confidence score, duplicate information, institution assignment, recommended solutions and current status.

---

## AI Workflow

The AI-powered backend consists of three major services:

**1. AI Analysis — `aiService.js`**

Uses the NVIDIA API and GPT-OSS-20B model to analyse citizen complaints, determine their categories, generate summaries and calculate classification confidence.

**2. Duplicate Detection — `duplicateService.js`**

Checks incoming complaints against previously submitted reports to identify potentially repeated problems.

**3. Institution & Solution Routing — `routingService.js`**

Uses available institutional datasets, category information and research-backed solutions to identify relevant institutions and recommend possible interventions.

The system also incorporates a human-review mechanism when the AI classification confidence falls below the configured threshold of 0.65.

---

## Future Scope

We envision expanding Sujh Bujh into a more comprehensive civic innovation ecosystem.

Potential future improvements include:

- **Multilingual Voice Reporting:** Allow citizens to report problems through voice input in regional languages.
- **Geolocation Integration:** Automatically identify the location of reported problems.
- **Image-Based Problem Detection:** Use computer vision to analyse uploaded photographs.
- **Advanced Analytics:** Identify recurring civic issues and geographical problem hotspots.
- **Institutional Collaboration:** Enable institutions to accept, manage and update assigned problems.
- **Real-Time Notifications:** Notify citizens about complaint progress and resolution.
- **Scalable Database:** Migrate from JSON-based storage to a production-ready database.
- **Deployment:** Make the platform accessible to citizens and institutions across Jharkhand.

---

## Expected Impact

Sujh Bujh aims to:

- Make civic problem reporting more accessible.
- Reduce repetitive and unorganised complaint submissions.
- Connect societal challenges with institutions that have relevant expertise.
- Encourage research-driven and practical solutions.
- Promote collaboration between citizens, educational institutions and local authorities.

**We believe that every problem deserves to be heard, understood and connected to a possible solution.**

---

## 👥 Team

**Project:** Sujh Bujh  
**Domain:** AI for Social Good | Civic Innovation | Smart Governance  
**Focus:** Jharkhand, India

---

*Built with the vision of transforming civic complaints into meaningful action.* 
