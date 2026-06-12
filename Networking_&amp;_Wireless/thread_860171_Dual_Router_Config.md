---
title: "Dual Router Config"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by Ocxic on 2008-07-15
I have 2 routers, one DSL Modem/router combo and a wireless router. heres my setup

Internet----->DSL Modem/Router(A) 10.0.2.0 255.255.255.0---->Wireless router(B) 10.0.4.0 255.255.255.0

I can get internet and ping all computers on the network from router B , but I cannot access any computers (ping or otherwise) on router B from router A

anyone have any ideas why this would be happening, I have a static route set in my DSL modem for 10.0.4.0

Destination: 10.0.4.0 Subnet mask 255.255.255.0 Gateway: 10.0.2.2

10.0.2.2 is the IP I've given router B on router A

---

### Post by NilsE on 2008-07-15
Most wireless routers have a built in firewall that prohibits inbound traffic.  Go into the wireless router configuration and find the options for opening inbound ports and open the necessary ports. You should be able to open all if the DSL router protects you from the outside.

---

### Post by Ocxic on 2008-07-15
that will work in that if i open port 22 for a specific computer and can ssh into that computer but i need to use the router ip 10.0.2.2 instead of the computers actual IP 10.0.4.10. and I can only open ports for one computer at a time.

---

### Post by issih on 2008-07-15
I'm pretty sure the routers are doing exactly what they should I'm afraid.

The job of a router is to take your local network, where we pretty much all use 192.xxx or 10.0.xxxx addresses and link that to the internet.

The whole point of a router is to allow this, without ending up with millions and millions of duplicate 192 or 10.0 addresses all popping up on the internet from all the little home networks.

Consequently from the wan side of a router, you do not see any of the lan directly, because that is exactly what the router is designed to prevent.

In essence you are seeing the exact same effect that means you can ping any web server on the internet, but you can't ping individual computer on your home network from the internet.

You can set up port forwarding rules, but that will not really solve your problem as you can probably only really send it to one specific computer connected to router B for each protocol.

You might be able to wangle this if you set both router to operate on the same subnet, e.g. 10.0.2.x, and ensured that dhcp is disabled in at least one of the routers. If you then connected from Router A to both the WAN port and a LAN port on router B then things might just work, as the switch on the back of B will know how to route to 10.0.2.x addresses on A. On the other hand you may just cause the world to implode :)

---

