# Network Intrusion Detection and Response


## Introduction
Network intrusion detection is a crucial aspect of cybersecurity. It involves monitoring and analyzing network traffic for signs of unauthorized access or malicious activity. This project aims to equip you with the skills to set up an Intrusion Detection System (IDS), detect network intrusions, and respond effectively.

## Pre-requisites
- Basic networking knowledge (IP addresses, subnets, ports, etc.)
- Familiarity with network security concepts
- Basic knowledge of Linux command line

## Lab Set-up and Tools

### Network Diagram

### Lab Environment Components
1. **Host Machine**: The primary machine used for setting up and managing the virtual environment.
2. **Virtual Machines (VMs)**: Simulated machines used to create the network environment.
   - **IDS VM**: A virtual machine running the Intrusion Detection System.
   - **Client VM**: A virtual machine representing a client within the network.
   - **Attacker VM**: A virtual machine simulating an external attacker.

### Tools
- **VirtualBox**: Open-source virtualization software by Oracle.
- **Ubuntu**: Linux distribution used for the VMs.
- **Snort**: An open-source network intrusion detection system (NIDS).
- **Wireshark**: A network protocol analyzer used for capturing and analyzing network traffic.
- **Metasploit**: A penetration testing framework used to simulate attacks.

### Setting Up the Lab Environment

#### 1. Install VirtualBox
- Download and install VirtualBox from the [official website](https://www.virtualbox.org/).

#### 2. Create Virtual Machines
- **IDS VM**: 
  - Create a new VM and install Ubuntu.
  - Install Snort:
    ```sh
    sudo apt-get update
    sudo apt-get install snort
    ```
  - Configure Snort for basic intrusion detection.

- **Client VM**:
-  Create a new VM and install Ubuntu.
  - Ensure it is connected to the same network as the IDS VM.

- **Attacker VM**:
  - Create a new VM and install Kali Linux.
  - Kali Linux comes pre-installed with Metasploit and other penetration testing tools.
    
Expected Output:

Snort running and logging alerts to the console or a log file.

### Task 2: Generating Network Traffic
Objective: Generate normal and malicious network traffic to test the IDS.

**Steps**:

1. On the Client VM, use tools like ping, curl, or iperf to generate normal traffic.
2. On the Attacker VM, use Metasploit to launch a simple attack:
```sh
msfconsole
use auxiliary/scanner/portscan/tcp
set RHOSTS <Client_VM_IP>
run
```
Expected Output:

Normal traffic logged by Snort without alerts.
Malicious traffic detected and logged by Snort with alerts.

### Task 3: Analyzing Network Traffic with Wireshark
Objective: Capture and analyze network traffic using Wireshark on the IDS VM.

**Steps**:

1. Start Wireshark and select the network interface to monitor.
2. Capture traffic while generating both normal and malicious traffic.
3. Use Wireshark filters to isolate and analyze specific types of traffic (e.g., ICMP, TCP SYN scans).

**Expected Output**:
- Captured network traffic with clear differentiation between normal and malicious traffic.
- Detailed analysis of packet contents and patterns.

### Task 4: Responding to Detected Intrusions
Objective: Respond to detected intrusions based on Snort alerts.

**Steps**:

1. Review Snort alerts and identify the type and source of the intrusion.
2. Implement network defenses such as:
     - Blocking the attacker's IP using iptables:
```
    sudo iptables -A INPUT -s <Attacker_IP> -j DROP
```
    - Modifying firewall rules to prevent similar attacks.
3. Document the incident and response actions.

**Expected Output**:

- Effective blocking of the attacker's IP.
- Enhanced network security through updated firewall rules.
- Comprehensive incident response documentation.
