---
title: "vlan connectivity"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by ub007 on 2008-06-26
Hello,

I've got 10 machines connected to a switch....
created vlans and grouped them as follows....
vlan2(port13,14,15) - 3 pcs
vlan3 - 3 pcs
vlan4 - 4 pcs

to start with i connected ubuntu server to port 13 of vlan2
and edited /etc/network/interfaces as follows
iface eth2 inet static

post-up vconfig add eth0 13
pre-down vconfig rem eth0.13
iface eth2.13 inet static
address 172.17.3.46
netmask 255.255.255.0
gateway 172.17.3.1

auto eth0.13

auto eth0


sudo /etc/init.d/networking restart

it takes the vlan ip.....
but the problem is i cant ping the switch anymore.....

is the configuration wrong?i've got only for NIC card(eth0),
intend to dish out ips to all 10 PCS via dhcp(making server member of all 3 vlans)....can anyone guide me plz...Thanks in advance..

Cheers
David

---

### Post by ub007 on 2008-06-26
To avoid any confusion,I have the 3 vlans configured on the switch but havent configured all the PCs yet.I tried to test the vlan connection by configuring the server first (port 13 of vlan 2).It doesnt ping the switch,so stuck at the first hurdle....

---

### Post by ub007 on 2008-06-27
I got that sorted out.....thanks

---

