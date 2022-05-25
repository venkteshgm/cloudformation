# infrastructure
Submission towards automation of AWS Networking VPC, 3 subnets, Internet Gateway and route table  
Creation of ec2 instance, RDS mysql and s3 bucket  
Load balancer routing requests sent to dns to auto scaler that scales up when cpu utilization goes over 5%  
and scales down when utilization is below 3%  
  
To run the automation script on the dev account, type the following command into the CLI in the current directory:  
aws cloudformation deploy --profile dev --stack-name test1 --template-file csye6225-infra.yml  
  
This will create an EC2 instance with default image  
  
To launch a VPC with our custom AMI, use the following command:  
aws cloudformation deploy --profile dev --stack-name test --template-file .\CloudFormation\csye6225-infra.yml --parameter-overrides imageId=image_id  
Example:  
aws cloudformation deploy --profile dev --stack-name test --template-file .\CloudFormation\csye6225-infra.yml --parameter-overrides imageId=ami-0a940db7ba3881ef0  
  
To delete the stack on the dev account, type the following command on the CLI in the current directory:  
aws cloudformation delete-stack --profile dev --stack-name test1  
  
In order to do the same for demo account, just replace dev with demo in the commands above

aws cloudformation deploy --stack-name test21 --template-file test2.yml --parameter-overrides imageId=ami-046ce0973d05c2038 BucketName=qwppizxcse profile=dev --region us-east-1 --profile dev --capabilities CAPABILITY_NAMED_IAM  
  
aws cloudformation deploy --stack-name test19 --template-file test.yml --parameter-overrides imageId=ami-046ce0973d05c2038 BucketName=qwmiijuwse ProfileName=dev CodeDeployBucket=codedeploy.dev.venktesh.me --region us-east-1 --profile dev --capabilities CAPABILITY_NAMED_IAM  


#cloudformation stack
  
aws cloudformation deploy --profile demo --stack-name test04 --template-file csye6225-infra.yml --parameter-overrides imageId=ami-0527b6df0e1ea7d89 BucketName=eguquvtyru CodeDeployBucket=venktesh-ami-bucket ProfileName=demo LambdaBucketName=venktesh-lambda-bucket --capabilities CAPABILITY_NAMED_IAM


aws acm import-certificate --certificate fileb://SSL/demo_venktesh_me.crt --certificate-chain fileb://SSL/demo_venktesh_me.ca-bundle --private-key fileb://SSL/privatekey.pem --profile=demo
