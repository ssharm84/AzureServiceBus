[# AzureServiceBus](https://www.youtube.com/watch?v=fmKY9wnUY28

Azure Message Bus:

1.A Service Bus topic provides an endpoint for sender applications to send messages.
2.A topic can have one or more subscriptions. Each subscription of a topic gets a copy of the message sent to the topic. 

Architecture:

 Microservice1										Microservice2	 

     Send	Topic(Send key)								Active Listener...Topic(listen key)								

		ServiceBus-key,data 
		
						MessageCount 1

As and when listener received data then Message Count becomes 0

Steps:
1.portal.azure.com
2.New Resource->Service Bus
3.Create namespace->ss-servicebus->Pricing=Standard->Create->Go to Resource->Create Topic=topic-ss
4.Click Topics under Entities and click topic-ss
5.Now create Subscriptions inside Service Bus-ss-sub...Max Delivery Count=10 and have all default and click Create
6.Now go to Shared Access Policies inside ss-servicebus
7.Click on Add and it will have 2 keys-Send key and Listen key
8.Select Send ->send-ss-key and click on Create
9.Now Select Listen ->listen-ss-key and click on Create
10.Both send and listen will have their own Connection Strings
11.Now have your Microservice1 from https://github.com/cpvariyani/azure-service-bus-send ...M2 from https://github.com/cpvariyani/azure-service-bus-listner.git
12.Inside your send microservice code, paste the Connection string from Send key and your topic name
13.Now once you send data from Send key, get into Topics-> and click your subscription->You can see 1 messages
14.Now configure your listen key in Microservice2 by copying Connection String and same topic name along with subscription name from your Shared Access Policies and pasting them in your code
15.Now run this listen key app and we should have Message Count to 0


	)
