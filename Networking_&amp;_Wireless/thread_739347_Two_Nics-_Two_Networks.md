---
title: "Two Nics- Two Networks"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by TherapyQuestionMark on 2008-03-29
Hi Guys.

I have two network cards installed on a machine running gutsy.

eth0 - gets ip via dhcp from cable modem
eth1 - gets ip via dhcp set to a static ip bound to the mac address

I want to set it up so that eth0 handles all internet related requests,
and eth1 handles all the internal network stuff.

here's my route-nr
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.36.32.0      0.0.0.0         255.255.240.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         10.36.32.1      0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth1

As I understand it, I need just one default route.

As it stands now, i have access to the internet, but I don't have access to my internal network.

Any idea how I can resolve this?

Any help is greatly appreciated.
Thanks!

---

