---
title: "I need to know what would be my network address"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by kustomjs on 2007-11-27
Hi Guys
I need to know what would be my network address?
ip address 192.168.20.5
netmask 255.255.255.0
network 192.168.??.?
Broadcast 192.168.20.255
Gateway 192.168.20.1

---

### Post by harrisony on 2007-11-27
your internal ip address (ip address for that computer in the lan) is 192.168.20.5
but for your external ip address (one that someone from the world can get to) you will need to go to a site like [http://ipchicken.com](http://ipchicken.com)

---

### Post by moyazes on 2007-11-27
Your network address will be '192.168.1.0'

with a netmask of 255.255.255.0 you have 256 addresses available in that range (0-255) .
2 of these addresses are needed for the network address and the broadcast address which gives you 254 available addresses for hosts on your LAN.

moyazes

---

