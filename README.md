# ELK-Project-1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

~/ELK-Project-1/Diagrams/Elk Network Topology.png 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs.

The configuration details of each machine may be found below.

| Name       | Function  | I.P. Address    | Operating System |
|------------|-----------|-----------------|------------------|
| RedTeamVM  | Gateway   | 52.170.59.36    | Linux            |
| Web1       | DVWA      | 10.0.0.5        | Linux            |
| Web2       | DVWA      | 10.0.0.6        | Linux            |
| ELK-Server | Filebeat  | 104.215.112.158 | Linux            |



### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the RedTeamVM machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 73.188.170.226

Machines within the network can only be accessed by 52.170.59.36    
A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed I.P. Addresses         |
|------------|---------------------|--------------------------------|
| RedTeamVM  | Yes                 | 73.188.170.226                 |
| Web1       | No                  | 52.170.59.36 104.215.112.158   |
| Web2       | No                  | 52.170.59.36 104.215.112.158   |
| ELK-Server | No                  | 10.0.0.5 10.0.0.6. 52.170.59.36|


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for faster and more consistent configuration.

The playbook implements the following tasks:
- Configures ELK-Server to use more memory
- Installs docker.io and python3-pip apt packages
- Installs the docker pip package
- Downloads the sebp/elk:761 docker container and configures the container to start with port mappings 5601:5601, 9200:9200, and 5064:5064.
- Starts the container and enables the container service to start on boot.


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

~/ELK-Project-1/Diagrams/Successful YAML file screenshot.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log changes and centralizes event data, preparing it for export to the ELK stack.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/filebeat/filebeat.yml
- Update the filebeat.yml file to include 10.0.0.5 and 10.0.0.6
- Run the playbook, and navigate to http:// 
104.215.112.158:5601/app/kibana to check that the installation worked as expected.

The following screenshot displays the result of successful installation. 
~/ELK-Project-1/Diagrams/Kibana Elk Metric.png


