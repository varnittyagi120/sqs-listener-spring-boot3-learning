# Amazon SQS Listener Project

This project demonstrates how to **consume messages from an Amazon SNS topic using an Amazon SQS queue**. The SQS queue is subscribed to an SNS topic, and a listener is built using **Spring Boot** to process any incoming messages.

---

## What is Amazon SQS?

**Amazon Simple Queue Service (Amazon SQS)** is a fully managed **message queuing service** that enables decoupling and scaling of microservices, distributed systems, and serverless applications. It allows messages to be reliably sent, stored, and received between components without losing messages or requiring each component to be always available.

---

##Project Overview

### ✅ SNS → SQS Integration
- This project listens to an **Amazon SQS queue** that is subscribed to an **Amazon SNS topic**.
- Any message published to the SNS topic is automatically delivered to the SQS queue.
- The **SQS listener** in this project consumes and processes those messages.

---

## 🔧 Technologies Used

- Java 17
- Spring Boot
- Spring Cloud AWS
- Amazon SQS
- Amazon SNS
- IAM (for secure access via keys)

---

##Configuration

Add the following to your `application.properties` or `application.yml`:

```properties
aws.access.key=YOUR_AWS_ACCESS_KEY
aws.secret.key=YOUR_AWS_SECRET_KEY
sqs.url=YOUR_SQS_QUEUE_URL
```

>**Important:** Never expose your AWS credentials in public repositories.

---

## 📥 How It Works

1. An **SNS topic** is set up with a subscription to an **SQS queue**.
2. This Spring Boot application connects to that **SQS queue**.
3. Whenever a message is published to the SNS topic:
    - It's forwarded to the subscribed SQS queue.
    - The **listener** in this app picks up and processes the message.

---

## 🚀 How to Run

1. Clone the repository.
2. Set up your AWS credentials and queue URL in the config file.
3. Run the application using any IDE or `./mvnw spring-boot:run`.
4. Publish a message to the SNS topic and watch it being consumed!

---

## 🔐 IAM Permissions Required

Ensure the IAM user has the following permissions:
- `sqs:ReceiveMessage`
- `sqs:DeleteMessage`
- `sqs:GetQueueAttributes`
- `sns:Subscribe`

---
