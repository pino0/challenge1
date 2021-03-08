# Challenge1 Static Website deployed to S3 AWS

I was using cloudformation so I created the template s3-cloudfront-template.yml
It will create a S3 Bucket a Bucket policy to controlling access to the bucket 
and I used cloudfront distribution to make this accessible to anyone on the internet,

To deploy this project in AWS follow this steps:

#Validate template cloudformation
aws cloudformation validate-template --template-body file://C:/Users/mmoncada/AWS/Challenge1/s3-cloudfront-template.yml

#Create Stack
aws cloudformation create-stack --stack-name challenge-01 --template-body file://C:/Users/mmoncada/AWS/Challenge1/s3-cloudfront-template.yml --capabilities CAPABILITY_IAM

#Check stack 
aws cloudformation describe-stacks --stack-name challenge-01

#Deploy
aws s3 sync --acl public-read --sse --delete C:/Users/mmoncada/AWS/Challenge1/endava-starter-website s3://challenge-01-s3bucket-17of2li38a10a
