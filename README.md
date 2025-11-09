
# 🧩 RetailStream — Real-Time Data Engineering Pipeline

RetailStream is a **real-time data streaming and orchestration pipeline** that simulates continuous retail event ingestion, processing, and storage using **Apache Kafka**, **PostgreSQL**, and **Apache Airflow** — all running in isolated **Docker** containers.

This project demonstrates how modern data engineering stacks integrate to handle **real-time event processing**, **data persistence**, and **automated workflows**.

---

## 🚀 Project Architecture


- **Kafka** handles real-time data ingestion and buffering.  
- **PostgreSQL** stores structured data for analysis and reporting.  
- **Airflow** orchestrates, schedules, and monitors data workflows.  
- **Docker Compose** ensures reproducibility and seamless multi-container setup.

---

## 🧠 Project Objective

To simulate and manage a **streaming retail data pipeline** that:

1. Continuously produces and consumes retail events (e.g., transactions, inventory updates).
2. Writes processed data into PostgreSQL for analysis.
3. Automates workflows (e.g., data validation, transformation) using Airflow DAGs.
4. Ensures end-to-end data reliability and traceability.

---

## 🏗️ Tech Stack

| Component | Purpose | Technology |
|------------|----------|------------|
| **Streaming** | Real-time event ingestion | Apache Kafka |
| **Storage** | Persistent structured data | PostgreSQL |
| **Orchestration** | Workflow automation & scheduling | Apache Airflow |
| **Containerization** | Isolated environment setup | Docker & Docker Compose |
| **ETL Scripts** | Data ingestion & transformation | Python |

---

## 📂 Project Structure

retailstream/
│
├── docker-compose.yml # Multi-container setup for Kafka, Postgres, Airflow
├── requirements.txt # Python dependencies
│
├── scripts/
│ ├── kafka_producer.py # Sends mock retail events to Kafka
│ ├── kafka_consumer.py # Reads events from Kafka and stores them in Postgres
│ ├── kafka_to_postgres.py # Integration script between Kafka and Postgres
│ └── start.sh # Helper script to start producer/consumer
│
├── airflow/
│ ├── dags/
│ │ └── kafka_check_dag.py # Airflow DAG for connectivity and monitoring
│ └── logs/ # Airflow logs
│
└── README.md # Project documentation


---

## 🔄 Data Flow Explanation

1. **Producer Stage**  
   - `kafka_producer.py` generates simulated retail transaction data.
   - Sends messages to a Kafka topic (e.g., `retail_events`).

2. **Kafka Broker Stage**  
   - Kafka acts as the message queue.
   - Stores and distributes data to consumers.

3. **Consumer Stage**  
   - `kafka_consumer.py` subscribes to the Kafka topic.
   - Parses and validates each event.
   - Inserts structured data into PostgreSQL.

4. **Database Stage**  
   - PostgreSQL stores all incoming events in tables (e.g., `retail_stream_data`).
   - Acts as the main data source for downstream analytics.

5. **Airflow Orchestration**  
   - DAGs run scheduled checks to monitor Kafka connectivity.
   - Automates data validation, transformation, and summarization tasks.

---

## 🧩 How Components Work Together

| Step | Component | Description |
|------|------------|-------------|
| 1 | Kafka Producer | Generates real-time retail events |
| 2 | Kafka Broker | Queues and distributes events |
| 3 | Kafka Consumer | Reads events and inserts into Postgres |
| 4 | PostgreSQL | Stores cleaned event data |
| 5 | Airflow | Automates validation, transformation, and reporting |

---


## ⚙️ Quick Start

```bash
# 1. Clone repo
git clone https://github.com/<yourusername>/retailstream.git
cd retailstream

# 2. Start all containers
docker-compose up --build

# 3. Access Airflow UI
http://localhost:8080  (username: airflow / password: airflow)

# 4. Run producer and consumer
docker-compose exec producer python /producer/kafka_producer.py
docker-compose exec producer python /producer/kafka_consumer.py

# Check data in Postgres:

docker-compose exec postgres psql -U postgres -d retaildb
SELECT * FROM retail_stream_data LIMIT 5;

```

##  🧩 Tech Stack
Component	Purpose
Apache Kafka	Real-time data ingestion & buffering
PostgreSQL	Persistent storage for events
Apache Airflow	Workflow orchestration & monitoring
Docker Compose	Multi-service environment setup
Python	Data producer, consumer, and ETL scripts

📘 Highlights

✅ Simulates a production-grade streaming architecture
✅ Demonstrates Kafka–Postgres integration
✅ Automates tasks via Airflow DAGs
✅ Fully containerized and reproducible setup

Author: Shravani Hariprasad

📧 shariprasad3296@gmail.com

🪄 Data Engineering | Real-Time Analytics | Workflow Automation

