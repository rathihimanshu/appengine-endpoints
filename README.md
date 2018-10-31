

After Creating a virtual environment.

Install the Endpoints Frameworks v2 library:

    
    
    $ pip install -t lib -r requirements.txt --ignore-installed
Deploying API

Generate an OpenAPI file by running: `python lib/endpoints/endpointscfg.py get_openapi_spec main.EchoApi --hostname [YOUR-PROJECT-ID].appspot.com`

Remember to replace [YOUR-PROJECT-ID] with your project ID.

Deploy the generated service spec to Google Cloud Service Management: `gcloud endpoints services deploy echov1openapi.json`

The command returns several lines of information, including a line similar to the following:

   Service Configuration [2016-08-01r0] uploaded for service "[YOUR-PROJECT-ID].appspot.com"
   
   
LOCAL ENVIRONMENT TESTING :-- 

-- dev_appserver.py ./app.yaml 

-- curl \
    --request POST \
    --header "Content-Type: application/json" \
    --data '{"message":"hello world"}' \
    http://localhost:8080/_ah/api/echo/v1/echo
    
DEPLOYING THE API BACKEND :--


Open the app.yaml file and in the env_varialbe section, replace [YOUR-PROJECT-ID] in [YOUR-PROJECT-ID].appspot.com` & service version as 2017-02-13r2

Then, deploy the sample --

do -- gcloud app deploy

Once deployed, you can access the application at https://your-service.appspot.com

curl curl \
    --request POST \
    --header "Content-Type: application/json" \
    --data '{"message":"hello world"}' \
    https://[YOUR_PROJECT_ID].appspot.com/_ah/api/echo/v1/echo
