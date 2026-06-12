---
title: "Configure ubuntu as router"
date: 2020-08-05
forum: Networking &amp; Wireless
---

### Post by neorob on 2020-08-05
Hello everyone

I'd like replace my router with a pc which is running ubuntu.
Actually my network is: ISP -> ONT (FTTH) -> ROUTER -> MYLAN
My goal is : ISP -> ONT (FTTH) -> UBUNTU SERVER (eth0) -> BRIDGE-eth1 -> MYLAN
ISP gives me this parameters to config the connection:

USER-VLAN: 835
Protocol: (PPPoE) PPP over Ethernet - (RCF 2516)
Encapsulation: 802.1Q
Primary and Secondary DNS: Server assigned
Username: myusername
Password: mypassword

How can I setup the connection on eth0?

I tried make a vlan with id 835 (eth0.835) and then run pppoeconf but it say no access concentrator has been found...

Any suggestion?

---

### Post by TheFu on 2020-08-05
Different ISPs have very specific requirements about this stuff. Around here, we can't completely remove the ISPs router from the connection, but after the initial validated connection is completed, it is possible to skip most of the traffic around their wimpy hardware with limited NAT capabilities.

For most non-networking-nerds, the risks of DIY routers is pretty high and pre-built router distros which run on the same hardware are a better choice. There are a number of reputable, maintained, x86 router distros which can be used.  Plus, the WAN router really needs to be a 100% stand-alone device for security reasons.  BSD and Linux solutions for routers are the most popular.  I use OPNSense on an APU2 system running an AMD x64 CPU.  OpenWRT has the typical web interface we all know, runs Linux, and can be maintained with weekly patching.  There must be 5 other reputable Linux router distros.

Ok - so I've said my peace - if you need more step-by-step stuff, not specific to PPPeE stuff, [https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)

Have fun, but be secure too!

---

