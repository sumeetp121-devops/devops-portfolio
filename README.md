# README - DevOps Portfolio Project

This is a complete end-to-end DevOps project that demonstrates all essential tools and practices used in real-world environments. The objective is to deploy a styled portfolio website using a full CI/CD pipeline and local Kubernetes infrastructure with monitoring and alerting.

---

## Project Objective
To deploy a simple HTML/CSS portfolio website using the following DevOps stack:
- **Git + GitHub** (Version Control & Repo Hosting)
- **Terraform** (Infrastructure Provisioning)
- **Ansible** (Server Provisioning & Automation)
- **Docker** (Containerization)
- **Kubernetes (Kind)** (Container Orchestration)
- **Prometheus + Grafana** (Monitoring & Visualization)
- **GitHub Actions** (CI/CD Pipeline)
- **Ingress + TLS** (Secure Access)

---

## Architecture Overview
- **Control Plane VM**: Ubuntu (Runs Kind cluster and CI/CD)
- **Worker Node VM**: CentOS (Managed via Kind)
- **Cluster CNI**: Flannel
- **Local Monitoring**: Prometheus + Grafana

---

## Step-by-Step Overview

### ✅ STEP 1: Git + GitHub
- Initializes a local Git repository
- Pushes a basic HTML/CSS portfolio website to GitHub

### ✅ STEP 2: Docker
- Builds a Docker image using nginx:alpine
- Runs and tests the image locally on port 8080

### ✅ STEP 3: Terraform
- Provisions 2 local VMs (Ubuntu & CentOS) using VirtualBox
- Ubuntu = control plane, CentOS = worker node

### ✅ STEP 4: Ansible
- Installs Docker, Kind, and Kubernetes tools on both VMs
- Starts Docker service and configures prerequisites

### ✅ STEP 5: Kubernetes (Kind + Flannel)
- Uses Kind to create a local cluster with 1 control and 1 worker node
- Installs Flannel CNI for networking between pods

### ✅ STEP 6: Deploy Portfolio to K8s
- Creates Kubernetes secrets for admin credentials
- Creates persistent volumes and claims
- Configures RBAC (service account + roles)
- Deploys the Docker container to the cluster using Deployment + Service

### ✅ STEP 7: Monitoring (Prometheus + Grafana)
- Installs kube-prometheus-stack via Helm
- Exposes Grafana on port 3000 and Prometheus on port 9090
- Auto-discovers nodes and workloads

### ✅ STEP 8: GitHub Actions - CI/CD
- Triggers on push to `master` branch
- Builds and loads Docker image to Kind cluster
- Applies latest K8s manifests to redeploy

### ✅ STEP 9: Prometheus Alerts
- Defines custom alert for high CPU usage
- Integrated with kube-prometheus-stack

### ✅ STEP 10: TLS Ingress
- Creates self-signed certificates using OpenSSL
- Deploys Kubernetes Ingress with HTTPS access
- Adds DNS entry to `/etc/hosts` for `portfolio.local`

### ✅ STEP 11: Backup & Restore
- Backs up all manifest files and Docker image
- Includes restore steps for disaster recovery

### ✅ STEP 12: Test Cases
- Verifies Kubernetes pods, services, secrets, PVCs, Prometheus/Grafana access
- Confirms alerts, secret injection, and web app availability

---

## Access Points
- Portfolio App: `http://portfolio.local` (via Ingress)
- Prometheus: `http://localhost:9090`
- Grafana: `http://localhost:3000` (Default login: admin/prom-operator)

---
# redeploy
