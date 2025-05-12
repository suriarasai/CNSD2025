# Simple Cloud Native Fullstack Application

This is a simple fullstack application built with a cloud-native approach, using Docker for containerization. It consists of a React frontend, a Node.js/Express backend, and a MongoDB database.

## Prerequisites

- Docker
- Docker Compose

## Getting Started

1.  **Clone the repository (if applicable) or ensure you have the project files.**
2.  **Navigate to the project root directory:**
    ```bash
    cd simple-cloud-native-app
    ```
3.  **Build and run the application using Docker Compose:**
    ```bash
    docker-compose up -d --build
    ```
    This command will:
    *   Build the Docker images for the frontend and backend services.
    *   Start the containers for the frontend, backend, and MongoDB services in detached mode (`-d`).

4.  **Access the application:**
    *   Frontend: Open your browser and go to `http://localhost:3000`
    *   Backend API (if you want to test it directly): `http://localhost:3001`

## Services

*   **Frontend:** A React application served by Nginx. It communicates with the backend service.
    *   Runs on `http://localhost:3000` (mapped from container port 80).
*   **Backend:** A Node.js/Express application providing a REST API. It connects to the MongoDB database.
    *   Runs on `http://localhost:3001` (mapped from container port 3001).
*   **MongoDB:** A NoSQL database used to store application data.
    *   Accessible within the Docker network at `mongodb://mongodb:27017/taskdb`.
    *   Host port `27017` is mapped to the container's port `27017` for direct access if needed (e.g., with MongoDB Compass), but the backend connects to it using the service name `mongodb`.

## Project Structure

```
simple-cloud-native-app/
├── compose.yaml        # Docker Compose configuration
├── backend/            # Backend service (Node.js/Express)
│   ├── Dockerfile
│   ├── package.json
│   └── server.js       # Main backend application file
├── frontend/           # Frontend service (React/Vite)
│   ├── Dockerfile
│   ├── package.json
│   └── ...             # Other frontend files (src, public, etc.)
└── README.md           # This file
```

## Technologies Used

*   **Frontend:** React, Vite, Nginx (for serving static files in Docker)
*   **Backend:** Node.js, Express.js
*   **Database:** MongoDB
*   **Containerization:** Docker, Docker Compose

## Stopping the Application

To stop all running containers, navigate to the project root directory and run:

```bash
docker-compose down
```

To stop and remove volumes (e.g., to clear MongoDB data):

```bash
docker-compose down -v
```

## Contributing

Feel free to fork this project and submit pull requests.

