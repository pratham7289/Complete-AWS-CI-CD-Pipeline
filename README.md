# CI/CD Pipeline Setup on AWS

## Overview

This project provides a step-by-step guide to set up a Continuous Integration and Continuous Deployment (CI/CD) pipeline on Amazon Web Services (AWS). The pipeline includes Code Commit for source code management, CodeBuild for building the application, CodeDeploy for deployment on EC2 instances, and CodePipeline for automating the entire process.

## Prerequisites

1. **AWS Account:**
   - Ensure you have an AWS account.

2. **IAM User:**
   - Create an IAM user with the `AWSCodeCommitPowerUser` permission.
   - Configure AWS-CLI on your local/virtual machine.

## Step 1: Code Commit Repository Setup

1. Create a Code Commit repository.
2. Optionally enable CodeGuru for code validation.
3. Retrieve HTTPS Git Credentials for Code Commit from IAM user Security Credentials.
4. Clone the repository locally using the provided credentials.
5. Create an `index.html` file, add your code, and push it to the remote repo.

## Step 2: Build Stage

1. Write a `buildspec.yml` file for the build process.
2. Create a CodeBuild project:
   - Choose AWSCodeCommit as the Source Provider.
   - Specify the repository and branch.
   - Configure build settings and artifacts.
   - Create the Build Project and start the build.

## Step 3: CodeDeploy

1. Create an Application and Deployment Group in CodeDeploy.
2. Install the CodeDeploy agent on the EC2 machine.
3. Create an `appspec.yml` file and push it to the repo.
4. Create scripts for NGINX in the provided repository link.
5. Start a deployment, providing the S3 bucket path.
6. Modify the EC2 instance's IAM role for `ec2-code-deploy` permission.
7. Restart the CodeDeploy agent on the EC2 instance.
8. Check if the deployment is successful.

## Step 4: CodePipeline

1. Create a CodePipeline:
   - Configure source provider as AWSCodeCommit.
   - Configure build provider as AWSCodeBuild.
   - Configure deploy provider as AWSCodeDeploy.
   - Review and create the pipeline.

## Files and Usage

- `index.html`: Your application code (simple HTML in this example).
- `buildspec.yml`: Defines the build process.
- `deployagent.sh`: Script to install the CodeDeploy agent on an Ubuntu machine.
- `appspec.yml`: Manages the deployment lifecycle on EC2 instances.

By following these steps and using the provided files, you can automate the building, testing, and deployment of your applications with AWS CI/CD.
