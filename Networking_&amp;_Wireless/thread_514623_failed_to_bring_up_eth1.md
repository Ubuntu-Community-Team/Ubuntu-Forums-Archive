---
title: "failed to bring up eth1"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by gforces6 on 2007-07-31
I installed Ubuntu server and I couldn't make it to bring up its second network card. Doesn't matter which card I use, it is working only that one that is connected to my ISP. ( dhcp).
My /etc/network/interfaces is shown like in the manual:
auto lo
iface  lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#primary - this one is for internet
auto eth0
iface eth0 inet dhcp

#this one should be for the lan
auto eth1
iface eth1 static
address 172.16.0.1
netmask 255.255.0.0
network 172.16.0.0
broadcast 172.16.255.255

Nevertheless, when I restart the network I end up with these 2 lines:
"don't seem to be have all the variables for eth1/inet
failed to bring up eth1"

One of the curiosities is that my ISP asigns as DNS a private address, namely 192.168.0.1
Any suggestion would be great!
Thanks!

---

### Post by scxtt on 2007-07-31
replace "iface eth1 static" w/ "iface eth1 inet static"

---

