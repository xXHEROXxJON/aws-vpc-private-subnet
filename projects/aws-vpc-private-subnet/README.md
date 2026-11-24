<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Creating a Private Subnet

**Project Link:** [View Project](https://nextwork.ai/projects/4e96e29d-98b8-551e-ae93-da39c36e30fd)

**Author:** Jonathon Davila

---

## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will create a private subnet, rout table, and network ACL.

### ✍️ What are we doing in this step?

In this step, I will be revisiting prior steps to setup my vpc and allow me to begin learning how to create private subnets.

### ✍️ What are we doing in this step?

In this step, I will create a private subnet to see the differences between hosting in a public and private setup.

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is a logically isolated virtual network within the AWS Cloud where you can launch and manage AWS resources. It is useful because it gives you complete control over your networking environment—including IP address ranges (CIDR blocks), subnets, route tables, and security layers like NACLs and Security Groups—allowing you to securely separate public-facing applications from private backend data.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create a public and private subnet

### One thing I didn't expect in this project was...

One thing I didn't expect in this project is that a VPC's default Network ACL allows all inbound and outbound traffic by default, meaning you have to explicitly create and attach a custom NACL to lock down a private subnet.

### This project took me...

This project took me about an hour.

## Private vs Public Subnets

The main difference between public and private subnets comes down to internet routing and accessibility. A public subnet has a route to an Internet Gateway (and typically auto-assigns public IP addresses), making it accessible from the internet for resources like web servers. A private subnet has no route to an Internet Gateway—keeping traffic internal to the VPC—so it can safely host sensitive backend resources like databases and member login data.

Having private subnets are useful because it keeps database items and other sensitive items frompublic access.

My private and public subnets cannot have the same ip address block.

### ✍️ What are we doing in this step?

In this step, I will create a private route table because like a public subnet needs a route table so does a private one.

![Private vs Public Subnets](https://nextwork.ai/hopeful_purple_peaceful_turkey/uploads/4e96e29d-98b8-551e-ae93-da39c36e30fd_afe1fdbd)

## A dedicated route table

By default, my private subnet is associated with local target.

I had to set up a new route table because it needs to be setup as private to not allow public internet access

My private subnet's dedicated route table only has one inbound and one outbound rule that allows traffic to flow strictly between resources inside the VPC, while blocking any direct traffic to or from the public internet since there is no route to an Internet Gateway.

### ✍️ What are we doing in this step?

In this step, I willl setup a private network ACL

![A dedicated route table](https://nextwork.ai/hopeful_purple_peaceful_turkey/uploads/4e96e29d-98b8-551e-ae93-da39c36e30fd_b4b904b5)

## A new network ACL

By default, my private subnet is associated with default ACL which allowed all inboundn and outbound traffic

I set up a dedicated network ACL for my private subnet to deny all traffic

My new network ACL has two simple rules - deny inbound and outbound traffic

![A new network ACL](https://nextwork.ai/hopeful_purple_peaceful_turkey/uploads/4e96e29d-98b8-551e-ae93-da39c36e30fd_1ed2cb07)
