# TechFlow Customer Support Multi-Agent AI System

This project is an AI-powered customer support chat system built for TechFlow Electronics.
It uses LangChain, LangGraph, Ollama (Llama3), and Retrieval-Augmented Generation (RAG)
to simulate a real customer support workflow.

The system helps customers who want to:

- Cancel their phone insurance
- Get technical help
- Ask billing questions

The chatbot intelligently routes users to the correct agent and tries to retain
customers before canceling their plan.

---

## Project Objective

The goal of this assignment is to demonstrate practical AI engineering skills by building
a system that:

- Uses multiple AI agents
- Uses real tools to process data
- Uses RAG to retrieve company policies
- Handles different types of customer conversations

---

## System Architecture

User Message
|
v
Greeter / Router Agent
(Intent detection + Customer lookup)
|
v
Problem Solver Agent
(Customer support / Retention offers)
|
v
Processor Agent
(Cancellation processing + status update)

---

## Agents in the System

### 1. Greeter & Orchestrator

Responsible for:

- Identifying customer intent
- Loading customer information
- Retrieving policy documents
- Routing the conversation to the correct agent

Supported intents:

- cancel
- tech_support
- billing
- unknown

### 2. Problem Solver Agent

Responsibilities:

- Offer retention discounts
- Explain Care+ benefits
- Provide troubleshooting help
- Answer policy questions using RAG

### 3. Processor Agent

Responsible for:

- Processing cancellations
- Updating customer status
- Logging actions to a file

---

## Tools Used in the System

### Customer Data Tool

Reads customer information from:
data/customers.csv

Function:
get_customer_data(email)

Returns:

- customer id
- customer tier
- subscription price
- signup date

### Retention Offer Tool

Generates retention offers using:
data/retention_rules.json

Function:
calculate_retention_offer(customer_tier, reason)

### Customer Status Tool

Processes cancellations and logs updates.

Function:
update_customer_status(customer_id, action)

Logs saved in:
outputs/status_log.txt

---

## RAG (Retrieval Augmented Generation)

The chatbot uses company policy documents to answer questions.

Documents:

- Care+ Benefits
- Return Policy
- Troubleshooting Guide

Location:
data/Policy Documents/

Steps:

1. Load documents
2. Split documents into chunks
3. Create embeddings
4. Store embeddings in FAISS
5. Retrieve relevant context during conversations

Embedding model:
nomic-embed-text (Ollama)

Vector database:
FAISS

---

## Technologies Used

- Python
- LangChain
- Ollama (Llama3)
- FAISS
- Pandas
- JSON
- Jupyter Notebook

---

## Project Structure

Customer Support Chat System
│
├── data
│ ├── Policy Documents
│ │ ├── care_plus_benefits.md
│ │ ├── return_policy.md
│ │ └── troubleshooting_guide.md
│ │
│ ├── customers.csv
│ ├── retention_playbook.md
│ └── retention_rules.json
│
├── outputs
│
├── techflow_multi_agent_support.ipynb
│
└── README.md

---

## Installation

Install required Python libraries:

pip install langchain langgraph langchain-community langchain-text-splitters faiss-cpu pandas python-dotenv

---

## Install Ollama

Download Ollama:
https://ollama.com

Then run:

ollama pull llama3
ollama pull nomic-embed-text

---

## Running the Project

1. Clone the repository

git clone https://github.com/yourusername/techflow-customer-support-ai.git

2. Open the project folder

3. Start Jupyter Notebook

jupyter notebook

4. Open the notebook:

techflow_multi_agent_support.ipynb

5. Run all cells

---

## Example Usage

run_chat("can't afford the $13/month care+ anymore")

---

## Test Scenarios

Test 1 – Financial Problem
"hey can't afford the $13/month care+ anymore"

Test 2 – Phone Problem
"this phone keeps overheating"

Test 3 – Value Concern
"paying for care+ but never used it"

Test 4 – Technical Issue
"my phone won't charge anymore"

Test 5 – Billing Question
"got charged $15.99 but thought care+ was $12.99"

---

## Key Features

- Multi-agent conversational system
- Tool-based data retrieval
- Retrieval Augmented Generation (RAG)
- Customer retention automation
- Realistic support workflow

---

## Author

AI Engineering Assignment  
TechFlow Electronics Customer Support Chat System
