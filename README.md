# Oauth2-Readme

## Basic authentication

- Basic authentication: 
+ Client access (resource) on server
+ Server request client type auth info (username, password)

- OAuth 1.0 and OAuth 1.0a:
+ Client request Authorization Server
+ Client login to server, server grant access for client and redirect to client  with parameter is oauth_verifier:
+ Server Resource call Authorization Server
```
    POST /oauth1/access HTTP/1.1
    Host: server.example.com
    Authorization: OAuth realm="Example",
                oauth_consumer_key="jd83jd92dhsh93js",
                oauth_token="hdk48Djdsa",
                oauth_signature_method="HMAC-SHA1",
                oauth_timestamp="123456789",
                oauth_nonce="7d8f3e4a",
                oauth_verifier="473f82d3",
                oauth_signature="..."
```

```
    Response:
    HTTP/1.1 200 OK
    Content-Type: application/x-www-form-urlencoded

    oauth_token=j49ddk933skd9dks&oauth_token_secret=ll399dj47dskfjdk

    body: 
        user :
            id: 1391238w734
            username: riddle
```
- Refs: 
    + [oauth1.wp-api.](https://oauth1.wp-api.org/docs/basics/Auth-Flow.html)
    + [medium](https://medium.com/apis-with-valentine/oauth-1-0-authorization-flow-using-flickr-api-and-postman-3-legged-oauth-c2a9b46bd8b9)
## Protocol Flow - three-legged flow

``` text
     +--------+                               +---------------+
     |        |--(A)- Authorization Request ->|   Resource    |
     |        |                               |     Owner     |
     |        |<-(B)-- Authorization Grant ---|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(C)-- Authorization Grant -->| Authorization |
     | Client |                               |     Server    |
     |        |<-(D)----- Access Token -------|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(E)----- Access Token ------>|    Resource   |
     |        |                               |     Server    |
     |        |<-(F)--- Protected Resource ---|               |
     +--------+                               +---------------+
```