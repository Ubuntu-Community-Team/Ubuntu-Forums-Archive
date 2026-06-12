---
title: "Port Forward With Two Routers"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by souteneur3190 on 2007-12-01
I have two routers in my network.  One is for VOIP (LinkySys) which is connected to my cable modem.  One is for the rest of the computers in the house (Netgear).  I am trying to forward ports to my computer for utorrent.  The internet connects fine but when I can never get a connection on any peer to peers because of portforwading.  I know I have to connect the LinkSys router directly to my computer to access the LinkSys configuration.  I think i have to forward the port (2202) to the Netgear router, then forward that same port to my computer.  Here is my problem, when I connect the computer straight to LinkSys the IP adress looks like this: 172.16.0.1.  When I incorporate and connect all the routers in the network I cannot access LinkSys and the netgear router ip address looks like this 192.168.2.1.  This changes the ip address of all the computers.  When I want to forward the port from LinkSys to Netgear, the LinkSys configuration only lets me forward to ip address that start with 172.16.0.x.  As I said before when i connect Netgear the ip address changes to 192.168.2.1.  How do I make my Netgear router have an ip address that looks like this 172.16.0.x?  I just one set of Ip addresses and if i need to make everything static i need to know what to put for the gateway address and the subnet mask.

---

### Post by Invalidx on 2007-12-01
I was wondering a similar thing, but for a different reason.
I'm getting a router for this room because I need more ports, and then I'd be through two of them to get to the internet, thereby messing up torrents.

---

### Post by froy02 on 2007-12-01
Your netgear router should connect from 1 of the ports on the linksys  to the uplink port of the netgear. The linksys router would assign all your DHCP adresses. The  address numbers would all be 172.16.0.xxx where xxx would be higher than 1. 
Your first router controls all your DCHP.  There should only be one DHCP control

After you connected your router as above  type "http://172.16.0.1" on your browser  and you can configure your DHCP addresses though I do not see the point of static address.

---

