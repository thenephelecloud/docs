---
description: >-
  The Service Level Agreements (SLAs) and Quality of Service (QoS) metrics are
  used to evaluate and monitor providers.
---

# SLAs and QoS metrics

These metrics ensure a consistent and reliable experience for data consumers while providing transparency and accountability for storage providers.

## SLA Definitions

The following SLA parameters define the minimum standards storage providers must meet. They will be indicated by the providers when creating a Storage Unit in the smart contract.

#### **1. Latency**

* **Definition**: The time it takes to complete a read or write operation.
* **SLA Requirement example**: Maximum average latency of **50ms** for read/write operations.

#### **2. Upload Speed**

* **Definition**: The speed at which data can be uploaded to the storage service.
* **SLA Requirement example**: Minimum speed of **10 MB/s** for uploads of files **1 GB or smaller**.

#### **3. Download Speed**

* **Definition**: The speed at which data can be downloaded from the storage service.
* **SLA Requirement example**: Minimum speed of **20 MB/s** for downloads of files **1 GB or smaller**.

#### **4. Uptime**

* **Definition**: The percentage of time the storage service is operational and accessible.
* **SLA Requirement example**: **99.95% uptime** over a rolling 30-day period.

#### **5. Error Rate**

* **Definition**: The proportion of failed operations (e.g., upload, download, or delete) compared to the total operations.
* **SLA Requirement example**: Less than **0.01% failed operations** per month.

## QoS Records

The QoS records serve as the backbone for evaluating SLAs. These records are continuously generated through monitoring and probing mechanisms.

#### **Structure of QoS Records**

Each QoS record consists of the following fields:

* **Timestamp**: The exact time when the record was created.
* **Provider ID**: A unique identifier for the storage provider.
* **Operation Type**: The type of operation being measured (e.g., read, write, upload, download).
* **Latency**: Measured latency for the operation.
* **Throughput**: Upload or download speed, depending on the operation type.
* **Success Status**: A flag indicating whether the operation succeeded or failed.
* **Error Details** (if applicable): A description of the error, if the operation failed.

#### **Data Collection Process**

QoS data is collected through a combination of:

1. **Probing Operations**: Automated test operations (e.g., uploading and downloading test files) to measure latency, throughput, and error rates.
2. **System Metrics**: Real-time monitoring of uptime and operational logs.

#### **High-Level Workflow**

1. **Probing**: Scheduled probes perform read, write, upload, and download operations at regular intervals.
2. **Measurement**: Each operation records its latency, throughput, and success status.
3. **Aggregation**: QoS records are aggregated over time to calculate averages, percentages, and trends.
4. **Validation**: Aggregated data is validated against SLA requirements found in the smart contract to determine compliance.
5. **Storage**: All QoS records are securely stored in a time-series database for long-term analysis.

#### **Reporting**

Summarized QoS rolling data will be sent to the Smart Contract for on-chain or Flashback frontend consultation.

Apart from that, other external mechanisms can be implemented to generate and send regular SLA compliance reports to Storage Providers based on custom periods.&#x20;

The summarized data includes:

* Average latency, upload speed, and download speed over the reporting period.
* Uptime percentage.
* Error rate statistics.

## Enforcement

Failure to meet SLA requirements may result in penalties or reduced reputation scores (as detailed in the Reputation System documentation). Providers are encouraged to consistently monitor their performance and address any deficiencies proactively.