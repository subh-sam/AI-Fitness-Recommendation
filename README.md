# 🏋️‍♂️ AI Fitness Recommendation System

## 📌 Overview
The **AI Fitness Recommendation System** is a backend-focused microservices project that provides personalized fitness recommendations based on user activity and fitness data.  
It follows modern backend practices such as **event-driven architecture**, **asynchronous messaging**, and **service-to-service communication**.

This project is designed to simulate a real-world fitness platform where different services work independently but communicate efficiently.

---

## 🧠 Features
- User activity tracking (workouts, calories, steps)
- Event-driven communication using Apache Kafka
- Personalized fitness recommendations
- Scalable microservices architecture
- Fault-tolerant and loosely coupled services
- Docker-based setup for easy deployment

---

## 🏗️ Architecture

---

## 🧩 Microservices Used

### 1️⃣ Activity Service
- Collects user workout and activity data
- Publishes activity events to Kafka

### 2️⃣ Recommendation Service
- Consumes activity events from Kafka
- Generates fitness recommendations

### 3️⃣ Notification Service
- Sends notifications (email / message) to users
- Triggered by Kafka events

### 4️⃣ Service Discovery (Eureka)
- Enables dynamic service discovery
- Removes hardcoded service URLs

---

## ⚙️ Tech Stack
- **Language:** Java 21
- **Framework:** Spring Boot
- **Architecture:** Microservices
- **Messaging:** Apache Kafka
- **Database:** MongoDB
- **Service Discovery:** Eureka Server
- **Containerization:** Docker
- **Build Tool:** Maven

---

## 🔄 Communication Flow
- REST APIs → Synchronous communication
- Kafka → Asynchronous event-based communication

---

## 📦 Kafka Topics
- `fitness-activity-events`
- `fitness-recommendation-events`

---

## 🐳 Docker Setup

### Run Kafka
```bash
docker run -d \
--name fitness-kafka \
-p 9092:9092 \
apache/kafka:4.1.1

//  Create Topic

kafka-topics.sh --bootstrap-server localhost:9092 \
--create --topic fitness-activity-events \
--partitions 3 --replication-factor 1

// Cumsumer message

kafka-console-consumer.sh \
--bootstrap-server localhost:9092 \
--topic fitness-activity-events \
--from-beginning
