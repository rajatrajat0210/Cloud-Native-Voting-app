# Kubernetes Voting App Deployment Guide

## Overview
This guide outlines the steps to deploy a voting application on Kubernetes using YAML manifests. The application consists of the following components:
- A frontend voting app
- A Redis queue
- A worker to process votes
- A PostgreSQL database
- A result app to display the results

## Summary

This project is a cloud-native web voting application where users can vote for their preferred programming language. It features a React frontend, a Go-based API backend, and a MongoDB replica set for data storage. The application is deployed on Kubernetes, utilizing various resources like Deployments, StatefulSets, Services, and Secrets for scalability, high availability, and security.

## Prerequisites
Ensure you have the following installed and configured:
- [Docker](https://www.docker.com/get-started)
- [Kubernetes (kubectl)](https://kubernetes.io/docs/tasks/tools/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/) (for local testing)

## Deployment Steps

### 1. Clone the Repository
```bash
git clone https://github.com/rajatrajat0210/Cloud-Native-Voting-app.git
cd Cloud-Native-Voting-app
```

### 2. Start Minikube (if using locally)
```bash
minikube start
```

### 3. Apply Kubernetes Manifests
#### Deploy Redis
```bash
kubectl apply -f redis-deployment.yaml
```

#### Deploy PostgreSQL
```bash
kubectl apply -f postgres-deployment.yaml
```

#### Deploy Worker
```bash
kubectl apply -f worker-deployment.yaml
```

#### Deploy Voting App (Frontend)
```bash
kubectl apply -f vote-deployment.yaml
```

#### Deploy Result App (Backend)
```bash
kubectl apply -f result-deployment.yaml
```

### 4. Verify Deployment
Check if all pods are running:
```bash
kubectl get pods
```
Check services:
```bash
kubectl get svc
```

### 5. Access the Application
Find the external IP of the voting app and results app:
```bash
minikube service vote --url
minikube service result --url
```
Open the URLs in your browser to interact with the application.

## Cleanup
To remove all resources:
```bash
kubectl delete -f redis-deployment.yaml
kubectl delete -f postgres-deployment.yaml
kubectl delete -f worker-deployment.yaml
kubectl delete -f vote-deployment.yaml
kubectl delete -f result-deployment.yaml
```
To stop Minikube (if used):
```bash
minikube stop
```

## Contributing
Feel free to fork the repository, make changes, and submit a pull request.
