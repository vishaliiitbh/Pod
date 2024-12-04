
Podcast Data Pipeline with Airflow
This project implements a data pipeline using Apache Airflow to automate the download and processing of podcast metadata. The pipeline fetches podcast episodes, parses the metadata, and stores it in a PostgreSQL database for easy querying.

Project Components
Key Features
Podcast Metadata Parsing: Downloads and parses XML metadata for podcasts.
PostgreSQL Integration: Saves parsed metadata into a PostgreSQL database.
Dockerized Setup: Uses Docker containers for Airflow and PostgreSQL services.
Files Overview
podcast_summary.py: Contains the Airflow DAG definition for the data pipeline.
Dockerfile: Configures the Docker image for the Airflow service.
docker-compose.yml: Defines and orchestrates the service containers.
Setup Instructions
Follow the steps below to set up and run the project on your local machine.

Prerequisites
Ensure you have the following installed:

Docker Desktop
Python (for writing/modifying code)
Step 1: Download the Project Files
Download the following files and keep them in a folder:

podcast_summary.py
Dockerfile
docker-compose.yml
Step 2: Create the Project Directory
Run the following commands in your terminal to create the required directory structure:

bash
Copy code
mkdir podcast
cd podcast
Step 3: Organize Project Files
Place podcast_summary.py inside a subfolder named dags.
Place Dockerfile and docker-compose.yml in the root directory (podcast).
Create additional subdirectories for logs and plugins:
bash
Copy code
mkdir dags logs plugins
mv podcast_summary.py dags/
Step 4: Build the Airflow Docker Image
Build the custom Docker image for Airflow using the following command:

bash
Copy code
docker build -t airflow-podcast .
Step 5: Start the Airflow Service
Start the Airflow containers using the docker-compose file:

bash
Copy code
docker-compose up -d
This will launch the Airflow web server, scheduler, PostgreSQL database, and other dependencies in the background.

Step 6: Access the Airflow Web UI
Open your web browser and navigate to:

text
Copy code
http://localhost:8080
Login using the default Airflow credentials:

Username: airflow
Password: airflow
Step 7: Configure the PostgreSQL Connection
Follow this guide to create a PostgreSQL connection in the Airflow UI:

Go to Admin > Connections.
Add a new connection:
Connection ID: postgres_default
Connection Type: Postgres
Host: <Postgres container host>
Port: 5432
Schema: <Database name>
Username: <Database username>
Password: <Database password>
Step 8: Run the Podcast Summary DAG
Locate the podcast_summary DAG in the Airflow web UI.
Turn it ON by toggling the switch.
Trigger the DAG to start the extraction, transformation, and loading process.
Notes
Check the logs in the Airflow UI if the pipeline encounters issues.
Modify podcast_summary.py to adjust the XML parsing logic or database schema as needed.