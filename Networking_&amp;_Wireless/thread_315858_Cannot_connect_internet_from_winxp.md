---
title: "Cannot connect internet from winxp"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by pkelkar on 2006-12-09
Hi,

I have installed ubuntu + dhcp3-server + shorewall with 2 nic. I have connected one nic to dsl modem. other nic is connected to gigabit switch which connects other pcs.

I am unable to browse internet from the client pcs (xp). I checked the ipconfig on xp. ipaddress/gateway/subnet looks okay to me. skype works on xp.

On linux box, in shorewall config if i specify eth0 as interfaces i cannot to internet. If I change eth0 to ppp0 the ubuntu box is able to connect to internet.

Are there any settings on shorewall or xp so that it can connect to internet. My shorewall settings are as follows.

interfaces
=======

net eth0 detect dhcp,routefilter,tcpflags
loc eth1 detect

Zones
=====
fw firewall
net ipv4
loc ipv4

Policy
====
loc net ACCEPT
$FW net ACCEPT
net all DROP info
all all REJECT info

Rules
====
DNS/ACCEPT $FW net
SHH/ACCEPT loc $FW
ping/ACCEPT loc $FW
ping/REJECT net $FW
ACCEPT $FW loc icmp
ACCEPT $FW net icmp
]

---

