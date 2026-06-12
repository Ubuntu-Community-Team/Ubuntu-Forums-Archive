---
title: "Wanting a second home network"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by ron45 on 2015-12-01
Hello all,
I am pretty new to networking yet extremely motivated in learning all I can (which isn't much so far....lol). I live in a large home that's divided into separate living spaces, meaning a shared house. There is a router/WAP that we all share in the home. I, however, want my own network to support my 4 devices. I have access/permission to configure the house router (Belkin AC1750) any way I view fit. I presently use a CAT5e that runs into my living space (as well as the sharedwlan). 

What I have in addition is a unmanaged switch w/ a uplink port, a hub w/ a uplink port (that I'm sure I won't need), and my own WAP. What I am unsure of are a few different concerns:

1) From the shared router, do I continue using the existing line and put my switch in after the router (in my space) or switch between modem and router which would require another switch in my living space.
2) The shared router has a default IP of of 192.168.2.1 and a sub of 255.255.255.0. I am able to change only the first and third Octets of the IP. Am I to understand that the sub configured that way only allows for one network and if so do I need to change it and if so, to what? 255.255.0.0?
3) How do I ensure that my network will be a totally separate entity? Do I need another machine as a server to accomplish that security?

Anything else I'm not thinking of?

Thx in advance!!

---

### Post by TheFu on 2015-12-04
If you want your network to be separate, get your own ISP.

If you can live with them controlling the WAN port, get your own router + firewall and make another subnet inside ... perhaps on the 10.x.x.x or 172.29.x.x subnets. However, whoever owns the WAN, always owns the traffic, so all your traffic WILL BE AVAILABLE to the other people with access to the router.  That is why people use VPNs and network encryption.

If this stuff isn't clear, there's a clear resource about "how the internet works" at grc.com/sn ... start with episode 25. Things should clarify - the stuff you know will be confirmed and the stuff you don't quite understand will be clear.  IPv4 networking isn't hard on this scale.  If you want/need to learn IPv6, there is free training and a cert from [https://ipv6.he.net/certification/](https://ipv6.he.net/certification/)

---

### Post by ron45 on 2015-12-15
Got it. Thanks

---

