# Architecture

:heavy_check_mark:_(COMMENT) Describe the complete architecture of your application and create a diagram like the one below. Link to it in this document._

![eShopOnContainers Architecture](https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/media/eshoponcontainers-development-architecture.png)

[Source](https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/introduce-eshoponcontainers-reference-app)


:heavy_check_mark:_(Beer Review App - Architecture) 
The beer reviewing application should be available for reviewer on a mobile device.
The mobile application that is available for the reviewer has a direct communication with the microservices.
On the other side a brewery should be able to login and add new beers to the list of beers in production and sale.
If worked out, every brewery should be able to access a web dashboard to maintain this list. In this assignment it's enought to be working with swagger.

One of the microservices we need is responsible for authentication and identity. 
This gives us the possibility to devide the user of the brewery to add, update and delete beers from the user who may add a review to a beer.

Given the identity it's possible to communicate with the beer microservice or the review microservice. 
The event bus wil give the identity to the correct microservice and send communication back to the right client app. 

The beer microservice and review microservice persist their own storage. But use the message bus to communicate.
Every beer needs to be seen by a user of the mobile application to leave a review to a beer. But can only do this once for a beer.
So the beer microservice needs to get a communication from the review microservice to know if that user already reviewed the beer from that brewery.

![Architecture_BrewApp](https://user-images.githubusercontent.com/74589688/193519111-c8ad1efb-6998-4955-9585-df427305bae9.png)
