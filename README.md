# TryHackMe---Traffic-Analysis-Essentials
## Introduction:
Network Traffic Analysis (NTA) is a fundamental security and operational methodology used to intercept, monitor, and analyze communication patterns to ensure system health and detect potential threats. By leveraging both Flow Analysis for high-level statistical summaries and Packet Analysis for Deep Packet Inspection (DPI), NTA provides the necessary visibility to identify the root causes of network anomalies. Ultimately, this practice allows organizations to establish comprehensive baselines for asset tracking and enhances their ability to detect and respond to malicious activities, ensuring both the security and performance of the network infrastructure.

## Finding the Flags:

## Flag 1:
### Step 1: Traffic Analysis
When the simulation starts, packet traffic begins and we detect two IPs that generate malicious traffic (represented by red):
<img width="796" height="594" alt="{4BF2513D-0E9D-43DC-9B01-A43185AEE63F}" src="https://github.com/user-attachments/assets/f7c88aa1-73f7-4a82-9e61-390553d145db" />

### Step 2: Identifying Malicious IPs
We found that the IPs: __10.10.99.99__ and __10.10.99.62__ are the ones that generate malicious traffic (the red dots):
<img width="797" height="561" alt="{C93F56B7-4247-41DC-8276-9F129C367CEE}" src="https://github.com/user-attachments/assets/1d12b41b-8fc3-426b-9b29-0c98ba798362" />

By applying filters in the IDS/IPS panel to block these IPs we get correct traffic and we get the first flag
<img width="471" height="366" alt="{8E43E195-3EF7-4C65-AB7B-B4DAC02907DF}" src="https://github.com/user-attachments/assets/61d20daa-e64a-47cd-a353-c1a2c118d689" />

## Flag 2:
### Step 1: Identifying Malicious Ports
According to this table we can identify three specific ports:
<img width="894" height="343" alt="{4D262EEF-D797-441A-A219-C8C8502450E3}" src="https://github.com/user-attachments/assets/aed76f5a-a148-4151-a31a-3d5bb3091a77" />
1. Port 4444: Commonly used as the default port for Metasploit listener shells and reverse connections.
2. Port 7777: Frequently associated with trojans and non-standard Command & Control (C2) communication.
3. Port 2222: Often used as an alternative port for SSH to bypass filtering or for malicious service masquerading.

### Step 2: Applying Filters:
After applying the filters to the ports mentioned above, we get the second flag:
<img width="476" height="371" alt="{F3E1C692-A268-4890-A941-F4F4E3F206D6}" src="https://github.com/user-attachments/assets/f8d3bc54-775b-4980-8ec1-5031facf7782" />

## Conclusions:
This laboratory highlighted the importance of correlating traffic logs with IDS/IPS alerts to identify network threats. By detecting malicious activity on non-standard ports specifically 4444 for Metasploit, 7777 for C2 traffic and 2222 for SSH masquerading, we were able to isolate IP 10.10.99.62. Implementing these filters successfully mitigated the attack and led to capturing the first flag. This exercise proves that deep packet inspection and port analysis are vital for effective incident response and network defense.
