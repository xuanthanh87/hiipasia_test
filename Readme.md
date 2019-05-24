## Setting up the Backend Server

+ **Create MySQL database**

	```bash
	mysql> create database test
	```

+ **Configure database username and password**

	```yml
	# spring-oauth2-backend/src/main/resources/application.yml
	spring:
	    datasource:
	        url: jdbc:mysql://localhost:3306/test?useSSL=false
	        username: <YOUR_DB_USERNAME>
	        password: <YOUR_DB_PASSWORD>
	```

+ **Specify OAuth2 Provider ClientId's and ClientSecrets**
	
	> This is optional if you're testing the app in localhost. .

	```yml
	## spring-oauth2-backend/src/main/resources/application-default.yml
	spring:
        security:
          oauth2:
            client:
              registration:
                google:
                  clientId: <GOOGLE_CLIENT_ID>
                  clientSecret: <GOOGLE_CLIENT_SECRET>
                facebook:
                  clientId:  <FACEBOOK_CLIENT_ID>
                  clientSecret: <FACEBOOK_CLIENT_SECRET>

	```

	*Please make sure that `http://localhost:8080/oauth2/callback/<provider>`* is added as an authorized redirect uri in the OAuth2 provider. For example, In your [Google API console](https://console.developers.google.com/projectselector/apis/credentials?pli=1), make sure that `http://localhost:8080/oauth2/callback/google` is added in the **Authorized redirect URIs**

	*Also, make sure that the above mentioned scopes are added in the OAuth2 provider console.*	For example, scope `email` and `profile` should be added in your Google project's OAuth2 consent screen.

+ **Run **

	```bash
	mvn spring-boot:run
	```

+ **API documents http://localhost:8080/swagger-ui.html*

## Setting up the Frontend Server

```bash
cd project home of FE
npm install && npm start
```