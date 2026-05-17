# Microservices-Task

## Overview
This document provides details on testing various services after running the `docker-compose` file. These services include User, Product, Order, and Gateway Services. Each service has its own endpoints for testing purposes.

## Microservices Task Project Overview

This project demonstrates a Microservices Architecture using Docker and Docker Compose.

The application consists of the following independent services:

- User Service
- Product Service
- Order Service
- Gateway Service

Each service runs inside its own Docker container and communicates through Docker networking.

---

# Architecture

![Architecture Diagram](images/architecture-diagram.png)

```text
                    +-------------------+
                    |      Client       |
                    +---------+---------+
                              |
                              v
                    +-------------------+
                    |  Gateway Service  |
                    |     Port 3003     |
                    +----+----+----+----+
                         |    |    |
            -------------    |    -------------
            |                |                |
            v                v                v

    +---------------+ +---------------+ +---------------+
    | User Service  | | Product Svc   | | Order Service |
    |   Port 3000   | |   Port 3001   | |   Port 3002   |
    +---------------+ +---------------+ +---------------+
```

---

# Technologies Used

- Node.js
- Express.js
- Docker
- Docker Compose
- REST API
- Microservices Architecture

---

# Project Structure

```text
Microservices-Task/
│
├── docker-compose.yml
├── README.md
│
├── user-service/
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
├── product-service/
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
├── order-service/
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
├── gateway-service/
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
└── images/
    ├── architecture-diagram.png
    ├── docker-running.png
    ├── user-service.png
    ├── product-service.png
    ├── order-service.png
    └── gateway-service.png
```

---

# Prerequisites

Before running the project, install the following:

## 1. Docker

Download:

https://www.docker.com/

Verify installation:

```bash
docker --version
```

---

## 2. Docker Compose

Verify installation:

```bash
docker compose version
```

---

# Step-by-Step Deployment

---

# Step 1 — Clone Repository

```bash
git clone <repository-url>
```

Move into project directory:

```bash
cd Microservices-Task
```

---

# Step 2 — Verify Files

```bash
ls
```

Expected:

```text
docker-compose.yml
user-service
product-service
order-service
gateway-service
README.md
```

---

# Step 3 — Build Docker Images

```bash
docker compose build
```

This command:
- Builds Docker images
- Installs dependencies
- Prepares containers

---

# Step 4 — Start All Services

```bash
docker compose up -d
```

Expected output:

```text
Creating network "microservices_default"
Creating user-service
Creating product-service
Creating order-service
Creating gateway-service
```

---

# Step 5 — Verify Running Containers

```bash
docker ps
```

Expected running containers:

| Container | Port |
|---|---|
| user-service | 3000 |
| product-service | 3001 |
| order-service | 3002 |
| gateway-service | 3003 |

---

# Docker Containers Screenshot

![Docker Running](images/docker-running.png)

---

# API Testing

---

# User Service

## Base URL

```text
http://localhost:3000
```

## Endpoint

### List Users

```bash
curl http://localhost:3000/users
```

Browser:

```text
http://localhost:3000/users
```

---

# User Service Screenshot

![User Service](images/user-service.png)

---

# Product Service

## Base URL

```text
http://localhost:3001
```

## Endpoint

### List Products

```bash
curl http://localhost:3001/products
```

Browser:

```text
http://localhost:3001/products
```

---

# Product Service Screenshot

![Product Service](images/product-service.png)

---

# Order Service

## Base URL

```text
http://localhost:3002
```

## Endpoint

### List Orders

```bash
curl http://localhost:3002/orders
```

Browser:

```text
http://localhost:3002/orders
```

---

# Order Service Screenshot

![Order Service](images/order-service.png)

---

# Gateway Service

## Base URL

```text
http://localhost:3003/api
```

## Gateway Endpoints

### Users API

```bash
curl http://localhost:3003/api/users
```

### Products API

```bash
curl http://localhost:3003/api/products
```

### Orders API

```bash
curl http://localhost:3003/api/orders
```

---

# Gateway Service Screenshot

![Gateway Service](images/gateway-service.png)

---

# Docker Compose Configuration

```yaml
version: "3.9"

services:

  user-service:
    build: ./user-service
    ports:
      - "3000:3000"

  product-service:
    build: ./product-service
    ports:
      - "3001:3001"

  order-service:
    build: ./order-service
    ports:
      - "3002:3002"

  gateway-service:
    build: ./gateway-service
    ports:
      - "3003:3003"
```

---

# Useful Docker Commands

## View Running Containers

```bash
docker ps
```

---

## View Container Logs

```bash
docker logs <container-id>
```

---

## Restart Services

```bash
docker compose restart
```

---

## Stop Services

```bash
docker compose down
```

---

## Rebuild Services

```bash
docker compose up -d --build
```

---

# Troubleshooting

---

## Port Already in Use

Check ports:

```bash
lsof -i :3000
```

Kill process:

```bash
kill -9 <PID>
```

---

## Container Not Starting

Check logs:

```bash
docker logs <container-id>
```

---

## Validate Docker Compose File

```bash
docker compose config
```

---

# Cleanup

Stop and remove containers:

```bash
docker compose down
```

Remove unused Docker resources:

```bash
docker system prune -a
```

---

# Final Validation Checklist

- Docker installed
- Docker Compose installed
- All containers running
- User Service working
- Product Service working
- Order Service working
- Gateway Service working
- APIs accessible
- No container crashes
- No port conflicts

---

# Future Improvements

- Kubernetes Deployment
- CI/CD Pipeline Integration
- Monitoring with Prometheus & Grafana
- Centralized Logging
- API Authentication
- Load Balancing

---

# Author

Santosh Kumar Sharma

## Services and Endpoints

### **User Service**
- **Base URL:** `http://localhost:3000`
- **Endpoints:**
  - **List Users:**  
    ```
    curl http://localhost:3000/users
    ```
    Or open in your browser: [http://localhost:3000/users](http://localhost:3000/users)

---

### **Product Service**
- **Base URL:** `http://localhost:3001`
- **Endpoints:**
  - **List Products:**  
    ```
    curl http://localhost:3001/products
    ```
    Or open in your browser: [http://localhost:3001/products](http://localhost:3001/products)

---

### **Order Service**
- **Base URL:** `http://localhost:3002`
- **Endpoints:**
  - **List Orders:**  
    ```
    curl http://localhost:3002/orders
    ```
    Or open in your browser: [http://localhost:3002/orders](http://localhost:3002/orders)

---

### **Gateway Service**
- **Base URL:** `http://localhost:3003/api`
- **Endpoints:**
  - **Users:**  
    ```
    curl http://localhost:3003/api/users
    ```
  - **Products:**  
    ```
    curl http://localhost:3003/api/products
    ```
  - **Orders:**  
    ```
    curl http://localhost:3003/api/orders
    ```

---

## Instructions
1. Start all services using the `docker-compose` file:
   ```
   docker-compose up
   ```
2. Once the services are running, use the above endpoints to verify the functionality.

Happy testing!
