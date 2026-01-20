# skilemen_DevOps_project

---

DevOps Task – Backend Deployment Using Render

This repository contains my solution to the Skileman DevOps task.

The purpose of this project is to demonstrate how I would deploy and manage a simple backend service using practical DevOps practices that are suitable for an early-stage startup.

The focus is on:

Simplicity

Security awareness

Reliability

Clear communication



---

Project Overview

The backend is a simple Node.js (Express) application deployed on Render.

This setup demonstrates:

A basic CI/CD pipeline

Secure handling of environment variables

Simple monitoring and logging

Deployment thinking appropriate for an MVP


This is not an enterprise-level system, but a clean and reliable early-stage deployment.


---

System Architecture

At MVP stage, the system is intentionally simple:

Users
  ↓
Render Platform (Hosting + Traffic Routing)
  ↓
Node.js Backend (Express)
  ↓
PostgreSQL (Managed Database)

CI/CD Flow:

GitHub → GitHub Actions → Render → Live Application

Render manages HTTPS, traffic routing, and service restarts automatically, so there is no need to configure a separate load balancer at this stage.


---

Backend Setup

The backend is built using Node.js and Express.

Basic Project Structure

/project-root
  ├── index.js
  ├── package.json
  ├── .env
  └── .github/workflows/ci.yml

---

Environment Variables

All sensitive or configurable values are stored using environment variables.

Why this is important

Keeps secrets out of source code

Improves security

Makes configuration easier

Allows different values per environment


In Render, these variables are added through the Environment settings of the service.


---

CI/CD Pipeline

The CI/CD pipeline ensures that code changes are automatically checked and deployed.

How it works

1. Code is pushed to the main branch on GitHub


2. GitHub Actions runs basic checks


3. Render automatically redeploys the service


4. The updated version goes live if successful


---

Monitoring and Logs

Logs

Render automatically collects application logs

Logs are accessible from the Render dashboard

Useful for debugging and understanding system behavior


Monitoring

At MVP stage:

Render provides uptime and service health

CPU and memory usage are visible

External uptime monitoring tools can be added if needed


This gives enough visibility without adding unnecessary complexity.


---

Security Considerations

Some basic security practices applied:

HTTPS is enabled by Render

Secrets are stored as environment variables

No sensitive information in the repository

Database is not publicly accessible

Dependency updates can be monitored via GitHub


These are simple but important steps for a secure MVP.


---

Why This Design

This design was chosen because:

It is simple and easy to manage

It supports fast development

It avoids overengineering

It fits an early-stage startup environment

