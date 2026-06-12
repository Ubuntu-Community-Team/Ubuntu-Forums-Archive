---
title: "Ubuntu 14.04.2, &quot;ifup eth5&quot; -&gt; &quot;RTNETLINK answers: File exists&quot; but no extra gateway"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by theosib on 2015-10-24
Whenever I try to google this error:
RTNETLINK answers: File exists
Failed to bring up eth5.

The only answers I see are ones saying that you need to make sure there's no extra gateway entry.  But I don't have an extra gateway entry.  I've also tried adding "metric" lines, and nothing works.  Can anyone help me figure out what to do?  Here's my /etc/network/interfaces file:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto eth3
iface eth3 inet dhcp

auto eth4
iface eth4 inet static
metric 100
address 192.168.0.1
netmask 255.255.255.0
#broadcast 192.168.0.255
#gateway 192.168.0.1

auto eth5
iface eth5 inet static
metric 200
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
#gateway 192.168.1.1

post-up route del default dev eth4
post-up route del default dev eth5
post-up route add default dev eth0

---

