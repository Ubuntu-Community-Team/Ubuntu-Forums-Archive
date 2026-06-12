---
title: "VLANS returning packets"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by manuvaldi on 2007-11-15
Hi,

I have configured 3 vlans under eth0 interface in my ubuntu server 6.06. The three vlans has different addressing. my problem is that when i ping(for example) to my server from other machine packet arrive to the correct interface/vlan but returning packet go through other vlan according (of course) to the routing table.

what can i do?. 

thanks in advance

---

### Post by intelligentfool on 2007-11-15
post the ping results and vlan configurations.

---

### Post by manuvaldi on 2007-11-16
my problem is solved = iproute2

routing tables for each interface/vlan
my address for vlan are:

vlan1=10.10.10.100
vlan2=192.168.0.100
vlan3=10.10.12.100

ip ro add 0.0.0.0/0 via 10.10.10.1 table 101
ip ru add from 10.10.10.100 table 101

ip ro add 0.0.0.0/0 via 192.168.0.1 table 102
ip ru add from 192.168.0.100 table 102

ip ro add 0.0.0.0/0 via 10.10.12.1 table 103
ip ru add from 10.10.12.100 table 103



now my problem is with vlan3. my server do ping other machines in the vlan, but the othrer machines can't ping my server. all port are configured in the vlan3 correctly.

---

### Post by intelligentfool on 2007-11-16
you need to add a 255.255.255.0 mask to your 101 and 103 vlans, otherwise the server doesnt know which 10. network to forward traffic to..... they're both using the default 255.0.0.0 mask currently.

---

### Post by manuvaldi on 2007-11-19
All interfaces/vlans are configured with mask
vlan1=10.10.10.100/24
vlan2=192.168.0.100/24
vlan3=10.10.12.100/24

I found the solution with 3 new routes, one for each interface routing table.

ip ro add 0.0.0.0/0 via 10.10.10.1 table 101
ip ro add 10.10.10.0/24 dev vlan1 table101
ip ru add from 10.10.10.100 table 101

ip ro add 0.0.0.0/0 via 192.168.0.1 table 102
ip ro add 10.10.10.0/24 dev vlan2 table102
ip ru add from 192.168.0.100 table 102

ip ro add 0.0.0.0/0 via 10.10.12.1 table 103
ip ro add 10.10.10.0/24 dev vlan3 table103
ip ru add from 10.10.12.100 table 103

---

