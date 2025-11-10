# MERN App on Kubernetes (Kubeadm)

This project deploys a 3-tier **MERN Stack** (MongoDB, Express, React, Node) application with a **Redis Cache** onto a Kubernetes cluster. The cluster is build  using **`kubeadm`**.

## 🛠️ Key Components

| Category | Technology | Purpose |
| :--- | :--- | :--- |
| **Cluster** | Kubernetes (`kubeadm`) | Orchestrates the application containers. |
| **Deployment** | Docker Images | Containerized Front End and Back End. |
| **Data Layer** | MongoDB + PV/PVC | Persistent data storage. |
| **Cache Layer** | Redis + PV/PVC | Session and response caching. |
| **Networking** | Calico CNI, CoreDNS | Enables Pod communication and service discovery. |

## 📁 Repository Structure

* `/frontend`: React source code and Dockerfile.
* `/backend`: Node.js/Express source code and Dockerfile.
* **/devops**: Contains all **Kubernetes YAML manifests** (Deployments, Services, PV/PVC) and cluster **setup scripts** (`.sh`).

## ⚙️ Deployment Flow

1.  **Setup:** Use scripts to install Kubeadm on Master and Worker EC2 nodes.
2.  **Containerize:** Build and push Front End and Back End Docker images to Docker Hub.
3.  **Deploy:** Apply all YAML manifests from the **/devops** folder using `kubectl apply`.
4.  **Access:** Application is exposed via a **NodePort Service** on the Worker Node's IP.
