# AWS CloudFormation Infrastructure Deployment

## Overview
This project demonstrates the deployment of a scalable AWS cloud infrastructure using AWS CloudFormation. The infrastructure includes a Virtual Private Cloud (VPC) with public and private subnets, EC2 instances, an Application Load Balancer, and Auto Scaling Groups.

## Prerequisites
- AWS account
- AWS CLI configured
- Basic knowledge of AWS CloudFormation

## Deployment Steps
1. Clone this repository to your local machine.
2. Navigate to the project directory.
3. Modify the CloudFormation template (`template.yml`) if necessary, updating parameters like region, prefix, etc.
4. Deploy the stack using the AWS CLI:
    ```bash
    aws cloudformation deploy --template-file template.yml --stack-name my-aws-infrastructure --capabilities CAPABILITY_IAM
    ```
5. Wait for the stack creation to complete.

## Components
### VPC
- The VPC is configured with public and private subnets across multiple availability zones.
- Internet Gateway is attached to allow internet access to instances in public subnets.

### EC2 Instances
- EC2 instances are launched within the public subnets.
- Instances have IAM roles attached for necessary permissions.
- User data scripts are provided to install AWS Systems Manager Agent and Amazon CloudWatch Agent.

### Load Balancer
- Application Load Balancer (ALB) is deployed to distribute traffic across EC2 instances.
- Listener is configured on port 80 to forward traffic to the target group.

### Auto Scaling
- Auto Scaling Group is set up to automatically scale the number of EC2 instances based on traffic load.
- Scaling policies can be adjusted as needed for optimal performance.

## IAM Roles
- IAM roles are created for EC2 instances with policies granting necessary permissions for Systems Manager and CloudWatch.

## Usage
- After deployment, access the application using the ALB DNS name.
- Monitor the instances and traffic using CloudWatch metrics and logs.

