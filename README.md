# Node.js CI/CD Pipeline using Jenkins, GitHub, and Docker

🚀 This project demonstrates a complete CI/CD pipeline setup for a Node.js application using:

- Jenkins (Freestyle job)
- GitHub (Webhook integration)
- Docker (Image build & containerization)
- AWS EC2 (Deployment)

## 🔧 Tools Used
- Jenkins on Ubuntu EC2
- GitHub (webhook-enabled repo)
- Docker
- Node.js sample app (not custom-built)

## 📦 Pipeline Workflow

1. ✅ **GitHub push** triggers Jenkins via webhook.
2. 🔄 Jenkins:
   - Pulls the latest code
   - Builds a Docker image
   - Stops and removes previous container (if exists)
   - Runs a new container

## 🔍 Commands used in Jenkins job

```bash
docker rm -f node-app-container || true
docker build . -t node-app-todo
docker run -d --name node-app-container -p 8000:8000 node-app-todo
