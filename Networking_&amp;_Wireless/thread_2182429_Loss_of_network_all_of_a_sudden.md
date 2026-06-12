---
title: "Loss of network all of a sudden"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by cable_guy on 2013-10-21
Hi all,

**Background to problem**

I use Ubuntu for my media centre (Actually XBMCBuntu if you are familiar) but all of a sudden on Friday I lost network connectivity on my HP Microserver N40L.

The last time I used it successfully it was Friday night and I added a load of NZBs to my SABNZBd queue, I remember at the time it was "chugging" a bit adding all these NZBs, but I realised it wasn't able to reach the news server.  The server's connected to a wifi router (which is acting as a switch but with DHCP turned ON) and has been stable for ~1 year

[B]
What I've tried
[/B]

[LIST]
[*]I eliminated hardware up to the router being the problem (I.E t is not the physical NIC or the cable)
[*]/etc/network/interfaces hasn't been touched, but I tried to set it to DHCP and it won't receive an address from DHCP either, with relevant ifdown and ifup being performed after changes were made
[*]I tried re configuring the router which the server is connected to to not use DHCP (giving the DHCP task to be handled by only the main router), it still didn't give me a DHCP address. Tried the server as static and still it can't see a network
[*]**When I connect the server to my other router, it gets a DHCP address OK**
[/LIST]



Thanks in advance for any tips! I am hoping anything will jog my memory or give me a "lead" !

solved: it was a hardware issue with a powerilne deeper in my network

---

