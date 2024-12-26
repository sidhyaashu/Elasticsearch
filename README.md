# Elasticsearch Setup with Docker and Python Environment

This project demonstrates how to set up and interact with an Elasticsearch instance using Docker and Python. It covers steps to launch Elasticsearch in a single-node setup and manage Python dependencies with Conda.

---

## 📋 Prerequisites

Ensure you have the following installed:
- [Docker](https://www.docker.com/) (Install Docker)
- [Conda](https://docs.conda.io/en/latest/) (Install Conda)
- [Python](https://www.python.org/) (Optional but included with Conda)

---

## 🚀 Quick Start Guide

### Step 1: Run Elasticsearch with Docker

1. Pull and run the official Elasticsearch Docker image in a single-node configuration:

    ```bash
    docker run -p 127.0.0.1:9200:9200 -d --name elasticsearch \
      -e "discovery.type=single-node" \
      -e "xpack.security.enabled=false" \
      -e "xpack.license.self_generated.type=trial" \
      -v "elasticsearch-data:/usr/share/elasticsearch/data" \
      docker.elastic.co/elasticsearch/elasticsearch:8.15.0
    ```

2. Verify that Elasticsearch is running by navigating to:  
   [http://127.0.0.1:9200](http://127.0.0.1:9200)

---

### Step 2: Set Up the Python Environment

1. **Create a new Conda environment:**

    ```bash
    conda create --name elastic_search python=3.11
    ```

2. **Activate the environment:**

    ```bash
    conda activate elastic_search
    ```

3. **Install the Elasticsearch Python client:**

    ```bash
    pip install elasticsearch
    ```

4. **Deactivate the environment (optional):**

    ```bash
    conda deactivate
    ```

---

## 🛠️ Features

- **Single-Node Elasticsearch:** Simplified setup with Docker for local development and testing.
- **Python Integration:** Install and manage the Elasticsearch Python client for API interactions.

---

## Use the Python client in your scripts:
```python
from elasticsearch import Elasticsearch

es = Elasticsearch("http://127.0.0.1:9200")
print(es.info())
```