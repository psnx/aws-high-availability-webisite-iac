# Udacity Cloud DevOps Engineer Nanodegree Program
## Project Deploy a high-availability web app using CloudFormation

The project consist of three files, and a text file to help with useful commands:
- `network.yml` describes the network infrastructure for the project
- `servers.yml` describes the `AWS::EC2` resource types, such as servers, load balancer etc.
- `network-params.json` describes the parameters referenced by the above `yml` files.

## Deployment:
0. Make sure that a role with `AmazonS3ReadOnlyAccess` exists in your IAM. This is called `UdacityS3ReadOnlyEC2` in the script (this must match the role you set up in your IAM)
1. Create the network like so: 
```bash
aws cloudformation create-stack --stack-name <your-network> --region us-east-1 --template-body file://network.yml --parameters file://network-params.json
```
Wait for the network to deploy and 
2. Create the `serevers`
```bash
aws cloudformation update-stack --stack-name servers --template-body file://servers.yml --parameters file://network-params.json --capabilities CAPABILITY_NAMED_IAM
```
Update the aboce command as needed, like the region.

