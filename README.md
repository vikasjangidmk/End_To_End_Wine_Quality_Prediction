# 🍷 End-to-End Wine Quality Prediction

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Conda](https://img.shields.io/badge/Conda-environment-brightgreen)
![AWS](https://img.shields.io/badge/Deployed-AWS-orange)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

An **end-to-end machine learning project** to predict wine quality based on its characteristics. This project is deployed using **AWS EC2** and **Docker** with **GitHub Actions CI/CD**.

---

## 🌟 Project Overview

This project is structured to create a full pipeline for predicting wine quality, from data preparation to model deployment. The model is built and evaluated locally, then containerized and deployed on AWS with CI/CD integration.

---

## 🔄 Workflows

1. **Update `config.yaml`**: Modify configuration settings.
2. **Update `schema.yaml`**: Define the data schema.
3. **Update `params.yaml`**: Set model parameters.
4. **Update the `entity` module**: Define data entities.
5. **Update configuration manager in `src` config**: Manage configurations.
6. **Update components**: Develop model components.
7. **Update pipeline**: Assemble data processing and model pipelines.
8. **Update `main.py`**: Execute the main script.
9. **Update `app.py`**: Deploy the application.

---

## 📊 Project Demo

![Project Architecture](static/assets/img/red_wine.jpg)
*Figure: Project pipeline and architecture diagram*

---

## 🚀 How to Run

### Steps:

1. **Clone the Repository**
    ```bash
    git clone https://github.com/vikasjangidmk/End_To_End_Wine_Quality_Prediction.git
    cd End-To-End-Wine-Quality-Prediction
    ```

2. **Create a Conda Environment**
    ```bash
    conda create -n mlproj python=3.8 -y
    conda activate mlproj
    ```

3. **Install the Requirements**
    ```bash
    pip install -r requirements.txt
    ```

4. **Run the Application**
    ```bash
    python app.py
    ```

---

## ☁️ AWS CI/CD Deployment with GitHub Actions

### Steps:

1. **Login to AWS Console**
   - Navigate to AWS Console and login.

2. **Create an IAM User for Deployment**
   - Grant specific access:
     - **EC2 Access**: For virtual machine management.
     - **ECR Access**: For storing Docker images in AWS.
   - Assign the following policies:
     - `AmazonEC2ContainerRegistryFullAccess`
     - `AmazonEC2FullAccess`

3. **Create ECR Repository**
   - Save the URI: `970547337635.dkr.ecr.ap-south-1.amazonaws.com/mlproj`

4. **Create an EC2 Machine (Ubuntu)**
   - This instance will host the application container.

5. **Install Docker on EC2 Machine**
    ```bash
    sudo apt-get update -y
    sudo apt-get upgrade
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh get-docker.sh
    sudo usermod -aG docker ubuntu
    newgrp docker
    ```

6. **Configure EC2 as Self-Hosted Runner**
   - Go to `Settings > Actions > Runners` in your GitHub repository.
   - Set up a new self-hosted runner and run the provided commands.

7. **Set Up GitHub Secrets**
   - Go to `Settings > Secrets` in your GitHub repository and add the following secrets:
     - `AWS_ACCESS_KEY_ID`
     - `AWS_SECRET_ACCESS_KEY`
     - `AWS_REGION = us-east-1`
     - `AWS_ECR_LOGIN_URI = 566373416292.dkr.ecr.ap-south-1.amazonaws.com`
     - `ECR_REPOSITORY_NAME = simple-app`

---

## 📁 Project Structure

```plaintext
├── config.yaml         # Configuration file
├── schema.yaml         # Schema definition
├── params.yaml         # Model parameters
├── src/                # Source code folder
│   ├── config/         # Configuration management
│   ├── entity/         # Data entities
│   ├── components/     # Model components
│   └── pipeline/       # Pipeline scripts
├── main.py             # Main script to run the pipeline
├── app.py              # Flask app for deployment
└── requirements.txt    # Required dependencies
