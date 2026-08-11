[Official Site Address](https://www.wloadctl.com)

# Wloadctl\-Service 8\.2 \| Global Enterprise Official Documentation

**Wloadctl** is a modern, enterprise\-grade workload automation and batch scheduling platform designed for cloud, on\-premises, and hybrid deployment environments\. This repository contains the core backend service of the Wloadctl platform, focusing on enterprise batch job scheduling, process orchestration, and intelligent task operation management\.

Built on the stable Spring Boot 3\.x ecosystem, Wloadctl provides visual workflow orchestration, distributed high\-concurrency job scheduling, full\-lifecycle task operation and maintenance, and fine\-grained permission governance\. It supports zero\-code multi\-database adaptation and multi\-scenario deployment, meeting standardized operation requirements for global enterprise environments\.

---

## ✨ Core Platform Capabilities

- **High\-Performance Scheduling Engine** — Powered by an event\-driven scheduling core, supporting cron timing, fixed interval polling, file event monitoring, webhook callbacks, and manual triggering\. It handles complex DAG workflow logic including serial\-parallel execution, conditional branches, job dependencies, mutual exclusion control, timeout interception, customizable retry policies, and SLA threshold monitoring\.

- **Distributed Scheduler\-Agent Architecture** — Decouples scheduling management from task execution\. Agent nodes can be deployed on Linux, Windows, and mainstream Unix\-like servers, supporting load\-aware task distribution and horizontal scaling to accommodate growing business volume\.

- **Full\-Coverage Job Type Support** — Natively supports Shell, Python, Java applications, SQL scripts, HTTP requests, file transfers, and custom executable programs, covering all common enterprise batch processing scenarios\.

- **Visual Drag\-and\-Drop Orchestration** — Features a web\-based graphical workflow designer with intuitive DAG editing, real\-time syntax validation, version control, and one\-click environment release, lowering workflow configuration costs\.

- **Multi\-Tenant \& RBAC Permission Governance** — Implements isolated workload management for multiple tenants and projects\. Standard RBAC authorization provides fine\-grained access control for menus, resources, and operations, with complete audit logs for full behavior traceability\.

- **Full\-Link Observability** — Delivers real\-time dashboards, workflow topology visualization, full execution tracing, centralized log query, and operational statistics\. Supports multi\-channel alerting via email and webhook for fast fault location and resolution\.

- **High\-Availability Cluster Support** — Stateless backend design enables enterprise\-level HA cluster deployment, ensuring stable and continuous scheduling service in production environments\.

- **Standard RESTful OpenAPI** — Provides comprehensive API interfaces for third\-party system integration, supporting programmable job triggering, status inquiry, workflow management, and data synchronization\.

---

## 🛠 Tech Stack

- **Runtime**: JDK 17 \(Mandatory\), Global UTF\-8 Encoding, Servlet 6\.0 Specification

- **Core Framework**: Spring Boot 3\.3\.5, Spring Framework 6\.1\.14, Spring Cloud 2023\.0\.2

- **Security**: Spring Security, JWT Stateless Authentication, BouncyCastle Encryption, Hutool Crypto Toolkit

- **Persistence**: MyBatis 3\.0\.3, MyBatis Plus 3\.5\.8, P6spy Full SQL Log Monitoring

- **Caching**: Redis Distributed Cache \+ Caffeine Local Secondary Cache

- **API Docs**: Knife4j 4\.4\.0 \(OpenAPI 3\.0 Compliant\)

- **Logging**: Logback Structured Logging with automatic archiving and cleanup policies

---

## 🗄 Multi\-Database Compatibility

Wloadctl supports zero\-code database switching via Maven Profile\. All database drivers are dynamically loaded at runtime without modifying business code, adapting to a wide range of global mainstream databases\.

- **Development**: H2 Embedded Database \(zero\-configuration startup\)

- **Open\-Source Databases**: MySQL 5\.7\+/8\.0\+, MariaDB, PostgreSQL 14\+

- **Enterprise Databases**: Oracle 19c/21c

- **Distributed Cloud Databases**: OceanBase \(MySQL/Oracle Mode\), TDSQL\-MySQL, TDSQL\-PostgreSQL

- **Specialized Enterprise Databases**: GBase, DM Database, Kingbase Database

---

## 🚀 Deployment Modes

Three deployment modes are provided to adapt to diverse enterprise environment requirements:

- **jar\-tomcat \(Default\)** — Built\-in Tomcat container, standalone Jar deployment, ready for most server and cloud environments

- **jar\-standard** — No embedded container, pure Jar deployment for professional third\-party middleware environments

- **war\-universal** — Standard War package for all Servlet 6\.0 compatible external containers

---

## ⚙️ Build \& Packaging Commands

```Plain Text
# Local Development & Testing (H2)
mvn clean package -Pjar-tomcat,h2

# Production - MySQL
mvn clean package -Pjar-tomcat,mysql

# Production - PostgreSQL
mvn clean package -Pjar-tomcat,postgresql

# Production - Oracle
mvn clean package -Pjar-tomcat,oracle

# Cloud Distributed - TDSQL / OceanBase
mvn clean package -Pjar-tomcat,tdsql-mysql
mvn clean package -Pjar-tomcat,oceanbase-mysql

# External Container War Deployment
mvn clean package -Pwar-universal,mysql
```

---

## 💻 Local Development Guidelines

### Environment Requirements

- JDK 17 \(required, incompatible with lower versions\)

- Maven 3\.6\+

- Local Redis service

### Startup Steps

1. Set project SDK and language level to JDK 17 in IDE

2. Start local Redis service

3. Run main class: `com.wloadctl.WloadctlServerApplication`

4. H2 database is enabled by default for local development

> **API Document Access Note**: Visiting `http://localhost:8080/doc.html` may return a **URL spelling error** prompt in Spring Boot 3\.x \+ Knife4j 4\.4\.0 environments\. This is caused by updated OpenAPI3 routing rules\. If inaccessible, use the standard OpenAPI JSON endpoint or adjust Knife4j path configuration to resolve the issue\.
>
> 

---

## 📁 Project Structure

```Plain Text
wloadctl-service/
├── bin/                # Deployment startup / shutdown / installation scripts
├── src/main/java       # Core source code
│   ├── annotation      # Custom annotations
│   ├── aspect          # AOP log and intercept logic
│   ├── configuration   # Global Spring configuration
│   ├── controller      # RESTful API layer
│   ├── domain          # Entity, DTO, VO and constants
│   ├── mapper          # MyBatis interfaces
│   ├── security        # Authentication and authorization
│   ├── service         # Business logic layer
│   ├── utils           # Common utilities
│   └── WloadctlServerApplication.java
├── src/main/resources  # Configurations, SQL and mapper XML
└── pom.xml             # Maven build and dependency configuration
```

---

## 📌 Production Deployment Specifications

- Production environments require JDK 17 exclusively

- External `config/` directory configurations take highest priority, supporting dynamic updates without repackaging

- Disable debug\-mode functions such as console SQL output and hot reload in production

- Match Maven database Profile with the actual production database type to avoid driver missing errors

- War deployment only supports Servlet 6\.0\+ containers \(incompatible with Tomcat 8/9\)

- Third\-party middleware deployment requires the `jar-standard` profile to avoid container conflicts

---

## 📄 Project Description

This project is an enterprise\-level backend service built for standardized development, iteration and deployment of internal business systems\.

