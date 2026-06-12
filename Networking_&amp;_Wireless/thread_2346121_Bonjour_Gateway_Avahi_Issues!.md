---
title: "Bonjour Gateway Avahi Issues!"
date: 2016-12-11
forum: Networking &amp; Wireless
---

### Post by laurieballard2 on 2016-12-11
Hi

So I have configured Avahi as per this guide:

[https://community.spiceworks.com/how_to/38251-build-your-own-bonjour-gateway](https://community.spiceworks.com/how_to/38251-build-your-own-bonjour-gateway)

The problem is that I am then unable to reach my Ubuntu machine on its IP address from any vlan other than its own.

So Eth0 has an IP address of 172.16.100.50 and DOES have a default gateway, so my default route is out Eth0

I then have Eth0.1, Eth0.10 and Eth0.50 respectively.
They have Ip addresses and  subnet masks in their correct subnets for the Vlan ID's but no default route.

I follow the guide and restart networking, BOOM I can no longer ping or access the 172.16.100.50 from any other Vlan!

If I get on the console and remove the Subinterfaces, I can then ping it fine from all vlans.

I suspect that if I ping from 10.100.10.50 (IP address on Vlan 10, i.e. Eth0.10 subnet) the Linux machine sees it has a directly connected interface on this subnet (Eth0.10) and tries to ARP for 10.100.10.50 out this subinterface instead of simply routing the ping reply back to the default route out Eth0.....but I could be wrong.

So basically, I can access 172.16.100.50 from a host on this VLAN but not hosts on other Vlans once I have followed the Bonjour/Avahi guide.

My switch is a Cisco, Vlan 100 (172.16.100.0/24) is the native untagged vlan and all other Vlans (1,10,50) are tagged on the switchport and its definitely a trunk.

Thanks!

---

