---
title: "Failover routing with iproute2"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by sambatyon on 2008-08-08
Hello,

I've searched for a solution to the following problem in the forum, and indeed a few guys had experienced it but I couldn't find a proper solution yet.

I have a laptop with both wired and wireless interfaces which is connected to a router which also serves as a gateway to the internet. I would like to use the wired interface as long as the cable is plugged in and switch to the wireless interface when the cable is unplugged.

I've looked in the iproute2 guide and defined the following table:

192.168.1.0/24 dev eth0  proto kernel  scope link  metric 1
192.168.1.0/24 dev eth1  proto kernel  scope link  metric 10
default via 192.168.1.1 dev eth0

I also set /proc/sys/net/ipv4/route/gc_timeout to 5 so the kernel will do a failover switching in short time.

I start pinging my router (192.168.1.1) when the cable is plugged and everything is OK. However, as I unplug the cable I wait and wait and I still get a "destination host unreachable".


Can anyone tell me what I'm doing wrong?

---

