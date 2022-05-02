# Service to deploy VPC - PROXY - RDS - LAMBDA
- *Help article:* https://montecha.com/blog/creating-an-rds-proxy-using-serverless-framework/
- *Repo:* https://github.com/montecha/examples/tree/main/serverless-framework-rds-proxy

## Overview
Connecting to a relational database from a Lambda function is challenging to get right. Your database can easily get overloaded by multiple Lambda invocations if the connection is not handled correctly and if the number of maximum concurrent connections gets exceeded. We use AWS' RDS Proxy service to make sure our Lambdas don’t run into these issues.
 - Put the Lambda in the same VPC as the RDS is in to connect to it.
 - Give internet access to Lambdas when they’re in a VPC.

**This creates several things:**
- 1 VPC
- 2 subnets which are created within the VPC
- 1 security group for our Lambdas which is also created within the VPC
- 1 security group for the RDS, which is also created within the VPC
- 1 RDS instance
- 1 Route
- 1 Route table
- 1 NAT
- 1 DB proxy
- 1 DB proxy target group
- 1 Role
- 1 Secret
- 1 Internet gateway

## Get started
**Requirements**
Have an aws account and credentials configured
Have serverless framework installed
**Deploy**
- Install dependencies: 
```bash
npm install
```
- Deploy in dev stage: 
```bash
serverless deploy stage --dev
```
- Deploy in prod stage: 
```bash
serverless deploy stage --prod
```

## Notes
- This service does not include prune plugin to prevent to delete previous version 