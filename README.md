# SOCR.AI

**Socratic Optimized Cognitive Responsiveness**

> Turning AI from an answer machine into a thinking partner.

SOCR.AI is an AI-assisted learning platform that integrates **Socratic Questioning** with **Large Language Models (LLMs)** to encourage learners to think, question, and reflect before relying on AI-generated answers.

The project addresses the emerging **AI Genie Phenomenon**, where increasingly capable generative AI can make obtaining answers effortless and potentially encourage cognitive offloading when learners rely on AI without sufficiently processing or evaluating information.

---

## Overview

SOCR.AI is designed around a simple principle:

```text
AI should not only provide answers.
AI should stimulate thinking.
```

Instead of immediately generating a final answer, SOCR.AI uses a Socratic interaction process to guide learners through questioning, reasoning, reflection, and understanding.

### Core Interaction

```text
User Question
      │
      ▼
Socratic Questioning
      │
      ▼
Reasoning & Reflection
      │
      ▼
LLM Assistance
      │
      ▼
Guided Understanding
```

---

## Key Features

### Socratic Questioning

Generates contextual questions that encourage users to examine assumptions, evidence, reasoning, and implications.

### Reasoning Analysis

Analyzes the learner's response to determine whether additional questioning or clarification is required.

### LLM Integration

Uses a Large Language Model as an assistance layer while maintaining the Socratic interaction mechanism.

### Learning Session

Organizes interactions into learning sessions so that conversations and learning progress can be tracked.

### Conversation History

Stores learning conversations and user responses for future review and evaluation.

---

## Architecture

SOCR.AI uses a service-oriented architecture combining **Go** and **Python**.

```text
                         ┌──────────────────┐
                         │    Frontend      │
                         └────────┬─────────┘
                                  │
                              HTTP / REST
                                  │
                                  ▼
                    ┌─────────────────────────┐
                    │      API Gateway        │
                    │           Go            │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │    Learning Service     │
                    │           Go            │
                    └────────────┬────────────┘
                                 │
                              gRPC
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │       AI Service        │
                    │         Python          │
                    └────────────┬────────────┘
                                 │
                    ┌────────────┴────────────┐
                    ▼                         ▼
             Socratic Engine                 LLM
                    │
                    ▼
             Guided Response
```

### Service Responsibilities

| Service | Technology | Responsibility |
|---|---|---|
| API Gateway | Go | API entry point and request routing |
| Learning Service | Go | Learning sessions, conversations, and business logic |
| AI Service | Python | AI processing and Socratic interaction |
| Socratic Engine | Python | Question generation, reasoning analysis, and response evaluation |
| LLM Layer | Python | Interaction with the selected language model |
| Database | PostgreSQL | Persistent learning data |
| Internal Communication | gRPC | Go–Python service communication |

---

## Project Structure

```text
SOCR.AI/
│
├── cmd/
│   ├── api-gateway/
│   ├── learning-service/
│   └── ai-service/
│
├── internal/
│   ├── gateway/
│   ├── learning/
│   └── ai/
│
├── ai/
│   ├── grpc/
│   ├── socratic/
│   └── llm/
│
├── proto/
│   └── ai/
│
├── pkg/
│   ├── logger/
│   └── config/
│
├── migrations/
├── scripts/
│
├── docker-compose.yml
├── go.mod
├── requirements.txt
├── .env.example
└── README.md
```

---

## Technology Stack

### Backend

- Go
- Fiber
- REST API
- gRPC

### AI

- Python
- Large Language Model
- Socratic Questioning
- Prompt Engineering

### Database

- PostgreSQL

### Infrastructure

- Docker
- Git
- GitHub

---

## Communication Flow

The application separates general backend processing from AI processing.

```text
Frontend
   │
   │ HTTP
   ▼
API Gateway
   │
   ▼
Learning Service
   │
   │ gRPC
   ▼
AI Service
   │
   ├── Socratic Question Generator
   ├── Reasoning Analyzer
   └── Response Evaluator
              │
              ▼
             LLM
```

This separation allows the AI processing layer to be developed independently from the main application backend.

---

## Environment Variables

Create a `.env` file based on `.env.example`.

Example:

```env
APP_ENV=development

HTTP_PORT=8080
GRPC_PORT=50051

DATABASE_URL=postgres://user:password@localhost:5432/SOCR.AI

AI_SERVICE_URL=localhost:50051

LLM_API_KEY=your_api_key
LLM_MODEL=your_model
```

**Never commit `.env` or API keys to GitHub.**

---

## Getting Started

### 1. Clone Repository

```bash
git clone https://github.com/your-username/SOCR.AI.git
cd SOCR.AI
```

### 2. Configure Environment

```bash
cp .env.example .env
```

Configure the required environment variables.

### 3. Install Go Dependencies

```bash
go mod download
```

### 4. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 5. Run with Docker

```bash
docker compose up --build
```

---

## Development

### Run API Gateway

```bash
go run ./cmd/api-gateway
```

### Run Learning Service

```bash
go run ./cmd/learning-service
```

### Run AI Service

```bash
python ./cmd/ai-service/main.py
```

---

## gRPC

The communication contract between Go and Python is defined in:

```text
proto/ai/ai_service.proto
```

After modifying the protobuf definition, regenerate the gRPC code using:

```bash
./scripts/generate_proto.sh
```

---

## Development Progress

| Component | Status |
|---|---|
| Project Architecture | 🟢 Completed |
| API Gateway | 🟡 In Progress |
| Learning Service | 🟡 In Progress |
| Socratic Engine | 🟡 In Progress |
| LLM Integration | 🟡 In Progress |
| gRPC Communication | 🟡 In Progress |
| Database | 🟡 In Progress |
| Prototype Validation | ⚪ Planned |

> Development status may change as the prototype evolves.

---

## Research Foundation

The development of SOCR.AI is motivated by research surrounding:

- Generative AI diffusion
- AI adoption in education
- Cognitive offloading
- Critical thinking
- Memory retention
- Socratic Questioning
- AI-assisted learning

Selected references include:

- Microsoft AI Economy Institute. *Global AI Adoption in 2025*.
- Chegg. *Global Student Survey 2025*.
- Rohilla et al. Research on AI dependency, memory retention, and critical thinking.
- Ramadhan et al. Research relevant to AI-assisted learning and cognitive processes.

Detailed references and evidence are presented on the SOCR.AI project website.

---

## Project Website

The SOCR.AI innovation showcase is available through the project website.

```text
https://SOCR.AI-profile-for-competition.vercel.app/
```
---

## Creator

**Rifqi Adli Hernawan**

IPB University  
Teknologi Rekayasa Komputer

Interested in:

- Information Technology
- Software Development
- Artificial Intelligence
- Educational Technology
- Research and Innovation

---

## License

This project is currently developed as an academic innovation prototype.

License information will be added when the project reaches the appropriate release stage.