---
title: "SoftEther local bridge missing VLAN ID"
date: 2018-10-17
forum: Networking &amp; Wireless
---

### Post by sky59 on 2018-10-17
Hi all,
not to make too much lines I go directly to the description:
SITUATION:
- I installed succesfully SoftEther v4.25 on OrangePiZero running OpenWrt ChaosCalmer 15.05.1 system, I crosscompiled using OpenWrt SDK environment for CortexA7
- I also instlalled SE on small router 4MB ROM/32MB RAM with help of extroot also using SDK for ramips

In both cases everything works except extroot and swapping memory is so slow that it is almost unusable
In both cases I used site-to-site configuration, one vpnserver and one vpnbridge, it simply makes xxxx km long ethernet cable over internet, no need any IP setting and so on...
Principle is that on vpnserver I need to make local bridge between virtual hub VPN and physical NIC interface like eth0
also on vpnbridge I make local bridge between virtual hub BRIDGE and physical NIC interface like eth0

then SoftEther connects together both VPN and BRIDGE virtual hubs, on first location I put LAN cable to eth0 NIC and on other location this cable "gets out" of eth0 ....

All connections virtual and local bridges got VLAN ID

Problem with Ubuntu is that I get VLAN ID only for virtual connection/session  BUT for local bridges I get no VLAN ID
This means that vpnserver and vpnbridge get connected over internet but system dos not work as there is some problem with local bridging...

Does anybody used SE with similar configuration? I tried 2 diffetent PCs and the same problem
Where should I start to look for the problem as to make local bridges to work?

---

### Post by sky59 on 2018-10-17
I add screenshots from SoftEther server manager, one is for working system with small router ramips, other is for PC wit Ubuntu 16.04 LTS

You can see that for Ubuntu some VLAN IDs are missing for local bridges

---

