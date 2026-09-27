# Event-Driven Commerce Platform

A portfolio microservices project demonstrating reliable asynchronous order
processing with Spring Boot, PostgreSQL, Apache Kafka, transactional outboxes,
idempotent consumers, compensating actions, Testcontainers, Docker Compose,
GitHub Actions, and Prometheus.

## Architecture

```mermaid
flowchart TD
    Client["API client"] --> Order["Order Service"]
    Order --> OrderDB[("Order PostgreSQL")]
    Order <--> Kafka["Apache Kafka"]
    Kafka <--> Inventory["Inventory Service"]
    Inventory --> InventoryDB[("Inventory PostgreSQL")]
    Prometheus["Prometheus"] --> Order
    Prometheus --> Inventory