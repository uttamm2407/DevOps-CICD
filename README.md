# End-to-End DevOps CI/CD Pipeline Project

## Project Overview

This project demonstrates an End-to-End DevOps CI/CD Pipeline using AWS EC2, GitHub, Jenkins, Docker, Docker Hub, and Kubernetes (Minikube).
The application is containerized using Docker, stored in Docker Hub, and deployed to Kubernetes. Jenkins automates the build and image push process.



#  Architecture


Developer
     │
     ▼
 GitHub Repository
     │
     ▼
 Jenkins Pipeline
     │
     ▼
 Docker Build
     │
     ▼
 Docker Hub
     │
     ▼
 Kubernetes (Minikube)
     │
     ▼
 AWS EC2




#  Technologies Used

- AWS EC2 (Ubuntu)
- Linux
- Git
- GitHub
- Jenkins
- Docker
- Docker Hub
- Kubernetes (Minikube)
- Nginx
- HTML
- CSS



#  Features

- CI/CD Pipeline using Jenkins
- Dockerized Web Application
- Docker Image stored in Docker Hub
- Kubernetes Deployment
- Kubernetes NodePort Service
- Hosted on AWS EC2
- GitHub Source Control



#  Project Structure


DevOps-CICD
│
├── index.html
├── about.html
├── style.css
├── Dockerfile
├── Jenkinsfile
├── deployment.yaml
├── service.yaml
├── README.md




#  CI/CD Workflow

1. Developer updates the code.
2. Pushes the code to GitHub.
3. Jenkins clones the repository.
4. Jenkins builds the Docker image.
5. Jenkins pushes the Docker image to Docker Hub.
6. Kubernetes deploys the Docker image.
7. Application becomes available on AWS EC2.

# Launch EC2

Ubuntu 24.04

t2.medium
20 GB Storage
Security Group
<img width="1573" height="495" alt="image" src="https://github.com/user-attachments/assets/fcb1619a-3977-459f-9698-772c9c13f22b" />

# File Permission
chmod 400 "KEY_NAME.pem"
ssh -i "KEY_NAME.pem" ubuntu@ec2-3-109-54-180.ap-south-1.compute.amazonaws.com

# Update Server
sudo apt update
sudo apt upgrade -y


### Installations

# Install Docker
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker ubuntu
newgrp docker

# Install Java
sudo apt install fontconfig openjdk-21-jre -y
java -version

# Install Jenkins
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update
sudo apt install jenkins -y
sudo systemctl enable jenkins
sudo systemctl start jenkins


#  Docker Image

Docker Hub Repository
uttamm2407/devops-app


Pull Image

command
docker pull uttamm2407/devops-app:latest



# Kubernetes Commands

Deploy Application

command
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml


Check Resources

command
kubectl get deployments
kubectl get pods
kubectl get svc


Restart Deployment

command
kubectl rollout restart deployment devops-app



#  Jenkins Pipeline

Pipeline Stages

- Clone Repository
- Build Docker Image
- Push Docker Image
- Deploy to Kubernetes


# 🌐 Application Access

During development with Minikube on AWS EC2, the application was accessed using Kubernetes Port Forwarding.

command
kubectl port-forward --address 0.0.0.0 service/devops-service 8081:80


Then open:

http://EC2_PUBLIC_IP:8081


> **Note:** Since Minikube is running inside an AWS EC2 instance using the Docker driver, the Minikube NodePort is not directly accessible from the internet. Therefore, `kubectl port-forward` was used to expose the application externally.



#  Project Screenshots

├── github.png
<img width="1900" height="847" alt="image" src="https://github.com/user-attachments/assets/cded0b74-5599-4aac-a624-e9b233817786" />

├── jenkins-dashboard.png
<img width="1917" height="840" alt="image" src="https://github.com/user-attachments/assets/6f43efea-348e-4ec1-aee9-6771485fd143" />

├── jenkins-success.png
<img width="1862" height="816" alt="image" src="https://github.com/user-attachments/assets/e7893829-86e8-4e6e-a013-a3f54a66b0e4" />

├── dockerhub.png
<img width="1907" height="790" alt="image" src="https://github.com/user-attachments/assets/d9008d95-84bc-4861-b56a-548af5830a1b" />

├── kubernetes-pods.png
<img width="935" height="135" alt="image" src="https://github.com/user-attachments/assets/9813979a-2286-4bea-9155-64ca655530f0" />

├── aws-ec2.png
<img width="1917" height="861" alt="image" src="https://github.com/user-attachments/assets/0bed52b2-4e79-4450-8e17-6418099f63f0" />

├── website-home.png
<img width="1915" height="932" alt="image" src="https://github.com/user-attachments/assets/b63c26ac-2dc6-4b62-98ed-cf3cc04ef0d2" />

├── website-about.png
<img width="1916" height="910" alt="image" src="https://github.com/user-attachments/assets/27afc6a0-abd6-46ba-b3af-a8b6c5cd1c60" />


# Author

**Uttam Pal**

GitHub:
https://github.com/uttamm2407

Docker Hub:
https://hub.docker.com/u/uttamm2407



Give this repository a ⭐ on GitHub.

