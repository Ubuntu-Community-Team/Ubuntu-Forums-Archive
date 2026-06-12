---
title: "Multiple Gateways"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by wag2639 on 2007-03-25
Hi

I'm pretty much a linux noob but I been winging my way through. 

So far, I've set upa Ubuntu Dapper 6.06 Server. 

In my apartment, I've got a weird setup. I got two ISPs, our main one is Road Runner and our secondary one is Verizon DSL. Theres a bunch of people in the apt but only me any my roommate use the DSL. 

I set up the network by having my primary router, which is connected to the Cable Modem, as a DHCP server (but I got it set up to give everyone a preassigned "static" ip) and my second router/DSL modem with its DHCP server off and a cat5 wired to connect both of them. 
My server is connected to the second router and everything works fine. 

However, since the primary router is setup as  the dhcp server, it is also the default gateway. 

So finally heres my problem/question?

How do I add the second router (192.168.1.2) as a "default" gateway and use metrics or whatever to get it to automatically choose the best route?

Also, whats the best way with the dual gateways to get it to use dyndns?

I looked online and read something about the route command but it doesn't seem to be resistant and I'm trying ez-ipupdate for the dyndns client.

Thanks

---

### Post by Mr. C. on 2007-03-25
The linux kernel does not use routing metrics.  This is for routing daemons only.

You will have to manually override the gateway.  I recently responded to a user's post about how to do this via script.  Please search the forums here for "mrc gateway script".

DHCP servers and gateways are independent.  A DHCP server can provide any default route or gateway.

Connecting both of your routers together, without being able to configure each of them to know about the other is a broken setup.  Routers must know about other routers on the network.

Since you have both routers connected, and if you change the default gateway, how will clients connected to the primary router be able to send via RoadRunner and the cable modem ?  All traffic will route via Verizon then.

> but it doesn't seem to be resistant 
I have no idea what this means?

MrC

---

### Post by wag2639 on 2007-04-01
I meant persistent.

---

