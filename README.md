# aws-apigateway-dynamodb-lambda
Playbook to publish Rest API on AWS API Gateway using Lambda and data from DynamoDB

Steps:
1. Create an AWS DynamoDB table
    * Make note of primary key
    * Make note or ARN
1. Create AWS IAM role
    * Use case: AWS Lambda
    * Permission: custom
      - Read -> Scan
      - Resources: Paste in DynamoDB ARN
    * Create role with custom permission
    * After creating the role, add another policy (AWS Managed Policy) called "AWSBasicLambdaExecutionRole"
1. Create AWS Lambda Function
    * Prefer Python but used Node.js because that's the code provided in Netlify tutorial
    * Make sure to attach IAM role created in previous step
    * Update the Lambda code to point to DynamoDB table
    * Update the Lambda code use DynamoDB method called "unmarshalled"
1. Create API using AWS API Gateway
    * Use configurations based on Netlify and/or AWS tutorial (e.g. Endpoint type: Regional or Edge Optimized)
    * Create resource
    * Enable CORS
    * Create GET request
      - Point to Lambda function created in earlier step
    

    
### References:
* Netlify Blog.  Creating an API with AWS: Lambda, DynamoDB, and API Gateway.  By Sarah Drasner VP Developer Experience.  https://www.netlify.com/guides/creating-an-api-with-aws-lambda-dynamodb-and-api-gateway/
* https://sarahdrasnerdesign.com/writing/
* AWS Hands-On Tutorial.  Build a Basic Web Application.  https://aws.amazon.com/getting-started/hands-on/build-web-app-s3-lambda-api-gateway-dynamodb/
* AWS IAM AWSLambdaBasicExecutionRole.  https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html
