# Service Desk Smart Assistant

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.7%2B-blue.svg)
![LangChain](https://img.shields.io/badge/framework-LangChain-green.svg)

A sophisticated LLM-powered service desk assistant built with LangChain that helps manage support tickets and schedule calendar events through natural language processing.

## 🌟 Features

- **Intent Classification**: Automatically determines user intent to route requests appropriately
- **Ticket Management System**: Create, update, and check status of support tickets
- **Calendar Integration**: Schedule and query calendar events
- **RAG (Retrieval Augmented Generation)**: Context-aware responses using vector similarity search
- **Conversation Fallback**: Graceful handling when direct tool execution fails

## 🛠️ Technologies

- **LangChain**: Framework for building LLM applications
- **Google Gemini 2.0**: Core language model powering the assistant
- **FAISS**: Vector database for efficient similarity search
- **HuggingFace Embeddings**: Sentence transformers for document embedding
- **Agents & Tools**: Task-specific functionality with ReAct prompting

## 📋 System Architecture

The assistant implements a comprehensive service desk system with:

1. **Vector Store**: Maintains separate collections for tickets and calendar events
2. **Tool Suite**: Specialized tools for different service desk operations
3. **Agent Executor**: Orchestrates tool selection and execution
4. **Intent Classification**: Routes user queries to appropriate handling logic
5. **RAG Pipeline**: Retrieves relevant context to enhance responses

## 🚀 Getting Started

### Prerequisites

```bash
pip install langchain langchain_openai langchain_community langchain_google_genai faiss-cpu sentence-transformers python-dateutil
```

### Directory Structure

```
service-desk-smart-assistant/
├── data/
│   ├── tickets.txt
│   └── calendar.txt
├── smart_service_desk_assistant.ipynb
└── README.md
└── LICENSE
```

## 💻 Usage Examples

### Creating Tickets

```
> I need to report a server outage in the east datacenter
Processing your request...

Created ticket #1001. Status: New
```

### Checking Ticket Status

```
> What's the status of ticket 1001?
Processing your request...

Found the following relevant tickets:
Ticket #1001: Server outage in east datacenter - Status: New - Created: 2025-05-20
```

### Updating Ticket Status

```
> Update ticket 1001 to In Progress
Processing your request...

Updated ticket #1001 status from 'New' to 'In Progress'.
```

### Scheduling Events

```
> Schedule a meeting with the IT team tomorrow at 2pm in Conference Room A
Processing your request...

Scheduled: IT Team Meeting for 2025-05-21 at 14:00 in Conference Room A
```

## 🧠 Core Components

### RAGDocStore

A dual-vector store system maintaining separate indices for tickets and calendar events, providing efficient semantic search capabilities.

### Tool Classes

- **TicketTool**: Manages ticket creation, status updates, and queries
- **CalendarTool**: Handles event scheduling and calendar lookups
- **ContextTool**: Retrieves relevant information from the knowledge base
- **DateTool**: Provides current date information for temporal reasoning

### Intent Classification

Uses a dedicated LLM chain to classify incoming queries into specific categories:
- ticket_creation
- ticket_status
- ticket_status_update
- schedule_event
- check_calendar
- check_current_date
- general_inquiry

### Agent System

Implements a Zero-Shot ReAct agent for reasoning about tool selection and use, with specialized prompting to guide the assistant's behavior.

## 🔍 Technical Details

- **Vector Embeddings**: Utilizes all-MiniLM-L6-v2 model for efficient semantic representations
- **Persistent Storage**: Maintains ticket and event data in simple text files
- **Error Handling**: Robust exception management with fallback to RAG-based responses
- **Conversation Flow**: Maintains context through well-formatted interaction patterns

## 📝 License

This project is licensed under the GNU GPL V3.0 License - see the LICENSE file for details.

## 🙏 Acknowledgments

- LangChain framework developers
- Google Gemini API team
- Sentence Transformers project
