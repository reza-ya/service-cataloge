
# 📞 CATI Backend Service Catalog

**Unit:** `SDU`  
**Version:** `1.1`  
**Last Updated:** `2025-02-10`

---

## 📄 Introduction
This document contains the service catalog for the **CATI Backend Service**, which is responsible for managing and processing **Computer-Assisted Telephone Interviewing (CATI)** operations.  
It handles:
- 📅 Interview scheduling  
- 📞 Call flow management  
- 📋 Questionnaire execution  
- 🔗 API integrations with other services

---

## 🎯 Scope
> This document and its content relate **exclusively** to the CATI Backend Service and apply only to the CATI platform.

---

## 🛠 Service Overview

The CATI Backend Service, as a **core component** of the platform, enables:
- Efficient execution of telephone-based interviews  
- Centralized management of interview data  
- Automation of interviewer allocation  

| **No.** | **Title**              | **Value**                                                                 |
|---------|------------------------|---------------------------------------------------------------------------|
| 1       | **Service Name**       | CATI Backend Service                                                      |
| 2       | **Brief Description**  | Execute, manage, and monitor CATI operations.                             |
| 3       | **Product Group**      | CATI Product Suite                                                        |
| 4       | **Service Status**     | Active                                                                 |
| 5       | **Availability**       | 7x24                                                                      |
| 6       | **First Release Date** | 2025-02-01                                                                |
| 7       | **First Version**      | V1.0                                                                      |
| 8       | **Last Release Date**  | 2025-02-10                                                                |
| 9       | **Last Version**       | V1.1                                                                      |
| 10      | **Service Importance** | High                                                                  |
| 11      | **Stability Rate (%)** | 98.5                                                                      |
| 12      | **Service Owner Unit** | PMU                                                                       |
| 13      | **Service Responsible**| SDU                                                                       |

---

## ⚙ Technical Specifications

| **Specification**         | **Value** |
|---------------------------|-----------|
| Position in Architecture  | Business Layer |
| Communication Channels    | REST API, AMQP |
| Service Scope             | Internal Network, Data Center, Internet |
| Service Provider          | Internal CATI Platform Team |
| Base Image                | Python 3.11 (Debian) |
| Build Image               | cati-backend:1.1.1 |

---

## 📋 RACI Chart

| Role / Unit  | PMU | POU | UIU | SDU | USER |
|--------------|-----|-----|-----|-----|------|
| CATI Service | C   | I   | A   | R   | Admin|

---

## 🔗 Service Dependencies

**Dependencies Guide:**

| No. | Level| Description                                               |
|-----|---------|-----------------------------------------------------------|
| 1   | H       | Service is unable to provide any services                 |
| 2   | M       | Service does not provide services correctly or fully      |
| 3   | L       | Service provides services but has internal system issues |
| 4   | Z       | Service fully and correctly performs its duties           |

**Services Dependent on CATI Service:**
| No. | Service Name       | Dependency Level | Description |
|-----|-------------------|------------------|-------------|
| 1   | PostgreSQL         | H                | Cannot operate without the database. |
| 2   | RabbitMQ           | M                | Required for real-time call events. |
| 3   | User Service       | M                | Required to fetch interviewer profiles. |
| 4   | Questionnaire Svc  | M                | Required for retrieving questionnaires. |

**Dependencies of CATI Service:**

| No. | Service Name       | Dependency Level | Description |
|-----|-------------------|------------------|-------------|
| 1   | PostgreSQL         | H                | Cannot operate without the database. |
| 2   | RabbitMQ           | M                | Required for real-time call events. |
| 3   | User Service       | M                | Required to fetch interviewer profiles. |
| 4   | Questionnaire Svc  | M                | Required for retrieving questionnaires. |

---

## 🧩 Core Functions

| No. | Function Name              | Type   | Description |
|-----|----------------------------|--------|-------------|
| 1   | `interview_schedule_create`| API    | Schedule a new interview. |
| 2   | `interview_status_update`  | API    | Update interview status. |
| 3   | `questionnaire_fetch`      | API    | Retrieve questionnaire details. |
| 4   | `questionnaire_submit`     | API    | Submit completed responses. |
| 5   | `interviewer_assign_auto`  | API    | Auto-assign interviewer. |
| 6   | `interview_results_process`| API    | Process interview results. |
| 7   | `call_flow_manage`         | API    | Manage automated call flow. |
| 8   | `reporting_export`         | API    | Export performance reports. |

---

## 🔄 Service Processes

1. **📅 Interview Scheduling Process**  
   - Trigger: New interview request  
   - Steps: Validate data → Assign interviewer → Save schedule → Notify via AMQP

2. **📋 Questionnaire Execution Process**  
   - Trigger: Interview start event  
   - Steps: Fetch questionnaire → Execute call flow → Store responses → Update status

3. **📊 Interview Results Processing**  
   - Trigger: Interview completion event  
   - Steps: Retrieve results → Process scoring → Store in database → Trigger reporting

---

## 👥 Final Stakeholders
- Call Center Operators  
- Interviewers  
- Supervisors  
- Data Analysts  

---

## 📝 Service Notes
> The CATI Backend Service is part of the **product service layer**, enabling **end-to-end automation** of telephone interviews.  
> Updates and modifications are possible based on product manager requirements.

---

## 📌 Service Changes

**V1.0** – Initial release with scheduling, questionnaire handling, and interviewer allocation.  
**V1.1** – Added reporting export, call flow management, and automated interviewer scoring.
