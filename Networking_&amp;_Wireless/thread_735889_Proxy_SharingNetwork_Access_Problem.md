---
title: "Proxy Sharing/Network Access Problem"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by chadraytay on 2008-03-26
Ok, so here's what I've got.

Internet access is coming in through a gateway tablet pc with a verizon wireless UM150 EVDO modem attached to it and connected as PPP0. The notebook then syncs up with my netgear router with its built-in intel wireless card.  I have the addresses set up so all computers always have the same ip from the router.

The other 2 laptops, and occasionally a PSP, are set to access through proxy on the first computer at 192.168.0.100

I'm running 3proxy to share the internet connection.

Anytime/Everytime that the other computers on the network are turned on and connected to the network, they get only a "server not responding" message when they try to connect.

However, the moment I go on the pc with internet access and pull up a terminal and do a "ping 192.168.0.OTHERCOMPUTERSADDRESS... the internet instantly starts working on the other pc.

This applies to 1 wireless computer, 1 wired computer, and my psp...

Can't seem to find anything wrong with the router. 3 proxy appears to be working every time...

Any clue why I have to ping my other network devices before they see the proxy server?:confused:

---

