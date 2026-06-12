---
title: "Need help with NIC and firewall configuration."
date: 2005-09-09
forum: Networking &amp; Wireless
---

### Post by otakuj462 on 2005-09-09
Hi, I posted a while ago about this, then was distracted by having two power supplies flame out on me. I guess this is the risk you run when working with 10-year-old scavenged hardware  ;-) 

I'm working to turn an old desktop PC into a router using Shorewall as my firewall software. The setup is like this: the box has two NICs, a wireless card ath0, and a wired ethernet card eth0. ath0 acts as a client to a wireless router, and eth0 is connected to an old laptop I have. Call the laptop's ethernet card eth1. The goal is to get the old laptop on the internet using the old desktop PC as a router.

I don't want to go to the trouble of configuring my old PC to act as a dhcp server, as it will only have one client connected to it. I therefore specify a static ip for eth0 using the following configuration:

auto eth0
iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
broadcast 192.168.2.255

The laptop is running Windows XP home. eth1 has a static ip address with the following configuration:

IP address:	192.168.2.100
Subnet mask:	255.255.255.255
Default gateway:     192.168.2.1

It seems like it would also be necessary to tell eth0, Shorewall, or both, what the ip address of eth1 should be. Is this correct? Is it possible to configure a network interface card in this way? Can anyone tell me where I can specify a destination address in Shorewall?


With my current configuration, neither box can ping the other, and the link lights don't even light up to indicate that there is a physical connection between the two cards. To me, this indicates that either eth0 or the firewall doesn't know it should be acting as a host to the laptop. Any hints as to what might be the problem and how to resolve it would be appreciated. Thanks.

-Jake

---

