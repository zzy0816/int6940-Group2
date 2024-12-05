1. Use a Twitter Developer Tool to create a project. 

  

   1.1 Use OAuth v2.0 to generate Client ID, and record access secret (not client secret). Use them to replace the environment variables in .env file.   

  

   1.2.1 In setting page, change User authentication settings, give right to Read, Write, and Direct Messages permissions, 

  

   1.2.2 Then, make type of app to native app, 

  

   1.2.3 lastly, change Callback URL and website URL to URL provided by EB in AWS that will get later. For now, use local URL like port:3000, you can also change Redirect             URL in. env this your local URL for now as well. 

    

2. In AWS. 

  

   2.1 Before you do anything, create a character in IAM and give it full access to DynamoDB, Lambda, API Gateway, and Elastic Beanstalk. Then, you will get an AWS Access          Key ID and AWS secret Access Key, make sure to generate new one by AWS as the one you set by yourself doesn't work. Use them to replace the environment                       variables in .env file. And remember to change all characters in the later setup to this character. 

  

   2.2 Use DynamoDB to create a Table, give it name "Posts", set Partition Key to "Posted" (if you change table name or key name, remember to change it in code files as             well). 

  

   2.3.1 Build a Lambda function with the name you want, then upload the PostHandler.zip (this is my Lambda name). 

  

   2.3.2 Then, you need to change the character to new character create before in configuration. 

  

   2.3.4 Lastly, set environment variable same as environment variables in .env files, it is in environment variable options under Configuration. Set key to variable key and             value to variable values. In the end, please test it to make sure that it works.  

  

   2.4 Build an API Gateway, choose type of rest API (I set a path Post Handler under main path which is empty name). Under this API, create two methods "post" and "get",           choose Lambda function you create before when you create method for both methods. Then, create a new stage "prod" and deploy this API to this stage (if use another           name, change "prod" in code files to your own). In the end, also don't forget to test these two methods to see if there are any problems. 

  

   2.5 Now, in Elastic Beanstalk, build a new environment (I called it Twitter-post), then upload the Final Code File. It will generate a URL in domain. Now, replace all            your local URL in .env file, Twitter developer tool's User authentication settings, Lambda function's environment variables to this URL. 

    

3. Debug tool 

  

   3.1 Use Postman to see the problem related with API like have problem with OAuth v1.1 or v2.0 in Twitter's API; AWS's API Gateway if you failed on test like can't get or          post posts. 

  

   3.2 In AWS, if you have problem, you can use CloudWatch to check what happened exactly, remember to give full access to Could Watch to the character you create. 

  

   3.3 If there are problems with deploying it to Elastic Beanstalk, you can download .ppk file and use PuTTY to login with SSH to access Elastic Beanstalk's console to             change nginx.conf files depending on the problem you meet. 

 
