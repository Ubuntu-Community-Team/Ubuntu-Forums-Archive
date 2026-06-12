---
title: "multiple isp"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by cocco on 2008-02-04
hi,with ubuntu it is possible to share multiple internet connections to have one fast single internet,and one network

as example i have now :
A (home connection DSL)
B (work connection DSL)
C (my sisters connection DSL)

A is connected to router1 witch shears internet to my 2 pc's
B is connected to router2 witch shares internet to 1 work pc
C is connected to accespointdslmodem witch is connected to sisters pc

it's possible to connect this 3 internet connections to have one single using a server or special router 
or software?? 

something like this 

A->router1-> home pc (cable), work pc (wifi),sisters pc(wifi)
B->router2->router1(wifi)
C->accespointdslmodem->router1(wifi)

---

### Post by gm04030276 on 2008-02-04
you can put a computer with say 3 network connections, one to each router and the other to the internal network and use it like a load balencer which is pretty much one fast connection between them all, or rather it shares the load between the two connections.

have a look at this
[http://www.samag.com/documents/s=1824/sam0201h/0201h.htm]("http://www.samag.com/documents/s=1824/sam0201h/0201h.htm")

---

### Post by cocco on 2008-02-04
ok i have understand ... theory
but as i'm new ..in ubuntu
don't know what a balancer do
and how it works...
so as i understand
i need
1 pc ( balancer)  with 1cable network card connexcted to home pc and 2 wireless cards connected to work and sisters router.
and then i have to set  up in the balancer..??
but now i need one more card to send back the connection.?
right?

and how is it?? is my connection 3 times faster?(like 3 dsl to 3mb = 9mb dsl?)

---

### Post by gm04030276 on 2008-02-04
I attached an image of how it would be setup, its not exactly your situation but i think its close.

You would essentially get a 9mb download speed then yes, but not to any one computer. Each computer would still only get max of 3mb/s but it would mean that say you have two computers on one connection that are always downloading lots of stuff and the other two connections are barely used, it would balence it out so that the two that are using lots get pretty much a connection to themselves and the others that aren't using much use the third one. Depends how much you use the internet, how much of a difference you would see and also how much you were trying to max out each connection.

---

### Post by perfecttao on 2008-02-04
Ok.....just for the record, load balancing just does that - it ensures that an equal (or close to!) amount of traffic is dispersed among connections.  You would not be able to use 9mbps on a single machine (as gm04030276 accurately points out).

You want to aggregate your internet links to give a far greater bandwidth.  This is known as channel bonding ([http://en.wikipedia.org/wiki/Channel_bonding](http://en.wikipedia.org/wiki/Channel_bonding)).  This is theoretically possible - in fact there are vendors in the UK who specialise in this ([http://www.interdart.co.uk/content/interdart/products/bondedBroadband](http://www.interdart.co.uk/content/interdart/products/bondedBroadband)) - and in theory you should be able to achieve this with the use of some clever routing and a gateway device using ifenslave that is simultaneously connected to all 3 internet links....although i'm not sure if it would work in practice as ifenslave is actually used for "switch style" port aggregation.

---

