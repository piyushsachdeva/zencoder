Write Terraform code to provision a complete AWS infrastructure with the following components:

Networking (VPC):

Create a VPC with DNS support enabled.
Provision public subnets and private subnets across multiple Availability Zones.
Attach an Internet Gateway for the public subnets.
Deploy a NAT Gateway with an Elastic IP in a public subnet to allow outbound internet access for instances in private subnets.
Configure Route Tables and associations for both public and private subnets to route traffic correctly.
Security Groups:

ALB Security Group: Allow inbound HTTP (port 80) and HTTPS (port 443) traffic from anywhere (0.0.0.0/0).
App Security Group: Allow inbound HTTP and HTTPS traffic only from the ALB Security Group. Allow all outbound traffic.
SSH Security Group: Allow inbound SSH (port 22) traffic (optionally restricted to a specific IP).
Load Balancing:

Provision an internet-facing Application Load Balancer (ALB) in the public subnets.
Create a Target Group for the application on port 80.
Configure an HTTP Listener on the ALB to forward traffic to the Target Group.
Compute & Auto Scaling:

Create a Launch Template specifying the AMI, instance type, and user data script. Ensure instances are associated with the App and SSH security groups.
Deploy an Auto Scaling Group (ASG) that launches instances into the private subnets.
Attach the ASG to the ALB Target Group.
Configure scaling policies, including simple scale-in/scale-out policies and a target tracking policy based on CPU utilization.
Set up a CloudWatch Metric Alarm to trigger scaling actions based on high CPU usage.
Storage:

Provision a private S3
bucket with versioning enabled.
* Enable server-side encryption (AES256) by default.
* Configure public_access_block settings to ensure the bucket remains private.
