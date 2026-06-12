---
title: "LAN Client unable to get to the INET"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by btaylor101 on 2007-06-13
I have Ubuntu 7.04 with a DHCP server installed. I have one Windoze client attached while I test. The client is able to  pull a valid ip adrs. I can ping myself 192.168.1.40, the router 192.168.1.1 as well as my eth0 67.9.xxx.xxx. When I tried to ping ubuntu.com it will not connect and when i try using the IP 82.211.81.158 it fails as well. I then backed up to the Linux box and was able to ping ubuntu.com as well the IP adrs. If anyone could give me a hand I would appreciate it.

---

### Post by Sendervictorius on 2007-06-13
I assume your Ubuntu 7.04 box is acting as a gateway to the internet. In which case have you set up network address translation (for example by installing and setting up firestarter)?

---

### Post by btaylor101 on 2007-06-13
I thought I had set up the NAT correctly using this statment:

[B]modprobe iptable_nat
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE[/B]

I must have missed something. I will look through the forums to get more info on NAT, unless someone already has a link handy.

---

