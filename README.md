## cloud_automation_with_ansible

Scenerio:
1. Lets say, there is a team of AWS cloud management and thier job is to configure, deploy and setup on the cloud.
2. When there is new projet comes, thos team is reponsible for setting up the configuration, regular changes, deplotment , and setting up the stack
3. When are talking about deployment on AWS, we talk about VPC.  Important role of the team is to set up the VPC in the AWS cloud to provide the security and high availability

#### Problem:
VPC consist of many moving parts. There are so many things to be considered when we are setting up the VPC. Subnets, NAT Gate way, Internet Gate way, ROute table, Security groups, NACL roles, EC2 and elastic ip etc.
- Bastion Host: Single point entry for puplic network into the private network

So, by condering the above problem, there is a human tendencyt to make mistake and reduce the lot of time.

#### Approach:
-  In order to reduce the time and track, we need to have a configuratin management of VPC
-  We also should have Automatic Setup 
-  There should be centralized change management system in order to control the changes
-  Version control ( Infastruction as a code- ansible)


#### Tool to be used:
- We will use Ansible for\
 a) AWS VPC set-ups\
 b) Bastion Host set-up which is used to Log in.\
 c) Deply the entire applicatin on AWS cloud 
 
 
 #### Process flow:
 - Login to AWS
 - Create an EC2 instance to run the anible playbook
 - Install Ansible
 - Inatall Boto
 - Setup EC2 role for Ansible , we are not going to use key pair which is less security
 - Create a project directory
 - Submit a sample cloud task with key pair
 - Create variables file for VCP and Bastom Host
 - Create VPC set up playbook
 - Create Baston Set up playbook
 - main.,yml playbook to call the playbook at once.



### Lets start working!!
Step1: Create EC2 instance in AWS console aand run below code in the *user data* section to install the ansible inside\
#!bin/bash
sudo apt update -y
sudo apt install -y ansible

NOTE: choose OS as ubuntu 20. , else follow the ansible doccumentation for ansible installation

Step2: Create a role and attach to the EC2:\


###### *Never ever ever use aws credential key in the code*

- create a role and give *admistrationacces*
- Go to the action of the instance and go to role modify
- select the role from the dro down and add
- 
