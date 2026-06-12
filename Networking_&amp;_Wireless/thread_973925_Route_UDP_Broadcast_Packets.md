---
title: "Route UDP Broadcast Packets"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by Fro_Bag on 2008-11-07
Hi,

I am in a situation where I would like to pass UDP broadcast packets over a router - ie from one IP subnet to another. The reason that we would like to do this is because our devices discover other devices present on a network via these broadcast UDP packets. Our network consists of several devices spread across several IP subnets.

I have several Ubuntu boxes running Ubuntu Server set up as routers. I am able to successfully route unicast IP packets. Is there a way to route these specific broadcast packets across the router too?

One of the solutions that I did try is a program called 'udp-broadcast-relay-0.3'. The problem with this program is that it must bind to the same port that my devices' stacks bind to. If I'm not running the stack, the software solves my problem. I have to be able to run my stack on these Ubuntu machines though.

Philip

---

### Post by kerpow on 2008-11-07
It seems that the only solution other than getting aditional 'servers' running on the individual broadcast domains would be to modify the existing stack running on the existing servers to use another protocol to comunicate to each other details of the devices they can see.  Can you modify or hook into the existing stack application?

---

### Post by Fro_Bag on 2008-11-07
Thank-you for your response.

Yes, I am able to - this is something I have considered, and I think this is the route that I am going to take.

I read on another forum that you can use iptables to allow broadcast traffic to be routed across a router. Does anyone know this can be achieved?

---

### Post by helgman on 2008-11-07
In "Cisco World" you have something command, ip helper-address, that let's you do this.

I think there is something simular in the "World of Linux", maybe something like this:

[http://linuxcommand.org/man_pages/dhcrelay8.html](http://linuxcommand.org/man_pages/dhcrelay8.html)

Regards,
Helgman

---

### Post by Fro_Bag on 2008-11-10
Thanks for that! I'll give this some consideration.

Another solution to this would be top use multicast addressing, and after some discussions, it looks like this is going to be implemented in our devices. I think that at the end of the day we need to do things correctly to ensure easy interoperability of future implementations of our protocol.

---

