---
title: "Losing network connection...."
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by bhathco on 2007-11-30
I using Gutsy, and it's cabled into a Netgear WPN824v2 router. When I boot the pc I get a dhcp address, no problem and can work with it pretty well. There have been occasion where I'll be working and the connection out will stop working.  Mostly, though, I'll step away from the PC for 1 hr or more and I'll come back to it not being able to connect to the net. I try and ping the router, and I get nothing. I try and ping the localhost(127.1), and nothing. It's only until I sudo dhclient, that I can get my connection back. BTW, I can ifconfig, while it's not working, and it says I have an IP address, so I don't get it. It's like the IP stack(or whatever) stops working, so it needs a dhclient kick in the ***. This is kinda annoying. Any thoughts? 

Thanks!

---

### Post by edm1 on 2007-11-30
i had a similar problem that was solved by [disabling IPv6]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html").

p.s. you should still be able to ping 127.0.0.1

---

### Post by AJB2K3 on 2007-11-30
Goto add/remove 
Install **network selector**
Disable the nm_applet in** System>preferances>sessions**
Add network selector** netapplet**
Restart


Clears low signal issue but speed is still a problem

---

### Post by bhathco on 2007-11-30
This machine is cabled, so it's not a wireless issue. As far as disabling IPv6, I can't see how that would affect. This is so much a performance problem, as it is a functioning problem.

---

