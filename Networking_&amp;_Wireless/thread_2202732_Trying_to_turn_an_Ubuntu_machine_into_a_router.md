---
title: "Trying to turn an Ubuntu machine into a router"
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by UrbenLegend on 2014-01-30
So I am trying to turn an Ubuntu machine into a wireless/ethernet router. I have three NICs installed on the machine:
[LIST]
[*]eth0: Connected to modem
[*]eth1: Connected to a switch
[*]wlan0: Setup in AP (aka hotspot or master) mode
[*]
[/LIST]

The idea is that any other computer can connect to the wireless hotspot or the switch and share the internet connection coming from eth0. I have added all the necessary connections using the Network Manager applet and currently it kind of works. The problem is that eth1 and wlan0 are on different subnets:
[LIST]
[*]eth1: 10.42.0.x
[*]wlan0: 10.42.1.x
[*]
[/LIST]
Therefore a computer connected to eth1 via the switch cannot talk to a computer connected to wlan0 via the hotspot. So while all computers can access the internet, it still doesn't quite behave like a regular router.

**How do I get both interfaces on the same subnet or somehow allow communication in between the subnets?** I've tried creating a bridge connection using Network Manager but it wouldn't let me activate it.
**I would prefer any solutions to use Network Manager rather than the old ifup ifdown interface.**

---

### Post by tfrue on 2014-01-31
I've never heard of using Ubuntu as a router, but I know of DD-WRT and SmoothWall are OSS for routers and PCs configured as routers. You might give those two options a look.

SmoothWall:
[http://www.smoothwall.org/](http://www.smoothwall.org/)

DD-WRT:
[http://www.dd-wrt.com/site/index](http://www.dd-wrt.com/site/index)

I did a Google search for Ubuntu as a router and here are two webiste that I found that may pertain to you.

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

[http://www.yourownlinux.com/2013/07/how-to-configure-ubuntu-as-router.html](http://www.yourownlinux.com/2013/07/how-to-configure-ubuntu-as-router.html)

Good luck,
Chris

---

### Post by ian-weisser on 2014-01-31
> **UrbenLegend said:**
> The problem is that eth1 and wlan0 are on different subnets:
[LIST]
[*]eth1: 10.42.0.x 
[*]wlan0: 10.42.1.x 
[/LIST]
Therefore a computer connected to eth1 via the switch cannot talk to a computer connected to wlan0 via the hotspot. So while all computers can access the internet, it still doesn't quite behave like a regular router.

**How do I get both interfaces on the same subnet or somehow allow communication in between the subnets?** I've tried creating a bridge connection using Network Manager but it wouldn't let me activate it.
**I would prefer any solutions to use Network Manager rather than the old ifup ifdown interface.**

That's right.
Network Manager is intended for desktop client, plus connection-sharing. It's really good at that.
But it's not designed to be a good bridge GUI, nor control router connections, nor lots of other use cases.

When I built a router from an Ubuntu Server, I did not use NM at all.

---

### Post by Doug S on 2014-01-31
My main Ubuntu server is also a router. I wouldn't know how to do it using Network Manager, as Ian mentioned, but then I have never used Network Manager. My LAN has wireless also, but I cheated for that part of it and configured my wireless router to be a switch (also it is located better for coverage than my server).

---

