# EventBroker

Turn any object/struct into a publish/subscribe event broker.

Importing

1. Clone repo and build
2. Copy framework into your target project.
3. In the Copy Files build phase add EventBroker.framework to the Frameworks Destination

Usage

EventBroker is a Protocol that allows developers to turn any object or struct into a publish/subscribe event broker. To implement, simply have a class or struct adapt the protocol and provide an implementation of the subscribedEvents property.

EventBroker instances are responsible for determinine when to publish an event. This condition is implementation specific.  When an event should be published, the EventBroker instance will call publish(event: with eventInfo:) to publish the event to subscribers.

publish(event: with eventInfo:) identifies all the subscribers to this event, then calls the handler for that subscriber.  eventInfo contains the data associated with the event.  It is passed as a dictionary [AnyHashable : Any]

Subscribers can then to subscribe to events published by the EventBroker by calling subscriber(event: subscriber:, handler:) The handler paramters is a closure that specifies the code to execute by the Subscriber when the event is published.  Subscribers must adaopt the Hashable protocol

Subscribers can unsubscribe to an event by calling unsubscribe(to event:, subscriber:)



