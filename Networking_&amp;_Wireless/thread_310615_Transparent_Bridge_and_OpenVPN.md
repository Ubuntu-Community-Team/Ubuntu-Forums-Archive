---
title: "Transparent Bridge and OpenVPN"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by mht on 2006-12-01
Hi there ,

this was my lan before **** happened:

LAN a ---L2 Foundry Switch A VLAN Port1---L2 Foundry Switch A VLAN Port2 --- LAN b

and now LAN a and LAN b arent in the same physical area anymore , so we need this :

LAN a --- L2 Foundry Switch A VLAN Port 1 --------eth0:eth1(box1) OPENVPN Transparent bridge (box2)eth1:eth0-------- L2 Foundry Switch B VLAN Port 1 --- LAN b 

Qs :

how would i config my openvpn box's eth0 to grab all traffic and send them to the remote box and vice versa ? promisc mode maybe ?

what should i do ? any hint is appreciated ](*,)

---

