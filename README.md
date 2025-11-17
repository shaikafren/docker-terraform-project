# docker-terraform-project
A Terraform project that provisions an NGINX Docker container using the Docker provider. Demonstrates IaC workflow with terraform init, plan, apply, destroy.
This project uses Terraform to provision an NGINX Docker container automatically.
Terraform connects to the Docker engine, pulls the nginx:latest image, and starts a container that exposes port 8080 on the host.

This shows how Infrastructure as Code (IaC) can manage containerized environments—replacing manual docker run commands with repeatable, automated Terraform scripts.
workflow Diagram:
              ┌────────────────────┐
              │   main.tf (IaC)    │
              │ - docker provider  │
              │ - nginx image      │
              │ - container config │
              └─────────┬──────────┘
                        │ terraform apply
                        ▼
           ┌────────────────────────────────┐
           │     Terraform CLI Engine       │
           │  - reads configuration         │
           │  - creates execution plan      │
           │  - calls Docker provider       │
           └──────────────┬─────────────────┘
                          │
                          ▼
          ┌─────────────────────────────────┐
          │        Docker Provider          │
          │ - Pulls nginx:latest image      │
          │ - Creates container             │
          │ - Maps port 8080 -> 80          │
          └────────────────┬────────────────┘
                           │
                           ▼
           ┌─────────────────────────────────┐
           │       Docker Engine             │
           │  Running Container: my-nginx    │
           │  Accessible: :8080              │
           └─────────────────────────────────┘

interview Questions with Answers
1.Interview Questions:
1.What is IaC?
A.Infrastructure as Code (IaC) is the method of defining and managing infrastructure using code instead of manual setup. It makes infra automated, repeatable, and version-controlled.
2.how dose terraform works?
terraform works by:
  1.reading configuration file (.tf).
  2.by creating an execution plan.
  3.communicating with providers(aws,docker,etc).
  creating,updating,destroying infrastructure based on the plan.
3.what is terraform state file?
A.terraform.tfstate file stores the current status of your infrastructure.
  terraform uses to know the resources exists and to determine future cases.
4.diffrence between apply and plan?
A.TERRAFORM PLAN:shows what paln is going to happen(preview).
 TERRAFORM APPLY: executes those changes and creates/updates infrastructure.
5.what are terraform providers?
A.providers are plugins that allows teraform to interact with AWS,DOCKER,GITHUB,ECT.
6.what is resource dependencys?
A.when one resource is dependent on another to be created first.
 terraform automatically manages these dependencys using the graph.
7.how do u handle secret variables?
A.a.use environment variables.
 b.use .tfvars files(never push to github).
 c.use vault/aws secrets manager.
 d.use terraform cloud varables.
8.EXPLAIN THE BENEFITS OF TERRAFORM?
A. Multi-cloud support
   Infrastructure automation
   Reproducible and consistent
   Version-controlled
   Easy to destroy/recreate
   Detects changes with plan



   IMAGE OF WELCOME TO NGINX! PAGE 
    http://44.220.44.106:8080


 
