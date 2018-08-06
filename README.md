# Moo - Task 2 - Deploy

### Ansible
  - Used Ansible Roles for Provisiong EC2 and Deploying Application
  - Used Ansible Vault for Storing AWS Access and Secret Key
  - Run Nginx and Application as docker containers inside EC2
  - Used site.yml file Provisiong EC2 and Deploying Application
  - Added Tags to all Resources Created in AWS
  
### Requirements
  - Provide Following input values:
  > aws_region: "eu-west-2"
  > vpc_id: "vpc-123456"
  > vpc_subnet_id: "subnet-123456"
  > ec2_instance_type: "t2.micro"
  > ec2_instance_image: "ami-123456"
  > ec2_assign_public_ip: yes
  > ec2_instance_count: 1
  > ec2_instance_key_pair: "devops-london"
  > ec2_user: "ubuntu"
  - Provide AWS Access and Secret Key as follows using Ansible Vault
  > Create Vault file inside roles/ec2/vars/main.yml 
```
ansible-vault create main.yml
```
  > Provide Vault Password and add entries as Follows 
 aws_access_key: 
aws_secret_key: 


### Ansible Role EC2
  - We can also Run EC2 Role using tag ec2 (or) provisioning
  - Used user data in EC2 for installing python
  - Added New EC2 Server to Ansible Inventory group using add_host
  - Waited for EC2 Instance to be available and SSH into it 
  
### Ansible Role Deploy
  - We can also Run Deploy Role using tag deploy (or) deployment
  - Created Config Directory for Nginx Config file
  - Installed Required Packages
  - Used template module for creating Nginx Config with proxy pass to application 
  - Launched Nginx and Application Container

### Command to run
- We need to provide Vault password while running playbook
```
ansible-playbook site.yml --ask-vault
```
   
### Steps for Production Ready
  - Will Created Ansible inventory with group_vars and host_vars for Prod ,Pre-Prod,Dev Environment
  - Will create ELB and R53 for Application
  - Will Created Deployment in Blue Green Strategy
  - Will Created Launch Configuration and ASG to run multiple EC2 instance in Different AZ
