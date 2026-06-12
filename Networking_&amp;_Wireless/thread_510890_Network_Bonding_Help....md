---
title: "Network Bonding Help..."
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by chr05210084 on 2007-07-27
Hello everyone... I have Ubuntu Server 7.04 installed in my server and I want to setup network bonding.
I have 2 static internet connection from 2 different ISP's and I have 3 NIC, I tried to follow the instructions here: [http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10) but its difficult to understand. I followed the instructions but I messed up.

My question is I want to bond my 2 internet connections to double the speed of my internet, how do I configure the IP's of the 2 internet connetion and how do I configure my local network connection? How do I put thier respective DNS? Is there any walkthrough in configuration of network bonding? Please help me.

[PHP]
My ISP1 IP is:
IP - 203.115.187.97
Subnet Mask - 255.255.255.0
Gateway - 203.115.187.1

My ISP2 IP is:
IP - 203.160.178.205
Subnet Mask - 255.255.255.224
Gateway - 203.160.178.193

and I want my local network IP to be:
IP - 192.168.5.1
Subnet Mask - 255.255.255.0
[/PHP]
Do I need to put a gateway in my local network connection? Where should I put their DNS?
How do I bond this? How do I configure this on /etc/network/interfaces, on /etc/modprob.d/aliases, and
/etc/modprob.d/arch/i386

Please help me guys please, I need to work it badly. Thank you very much.
Richard R. Cahilig

---

### Post by webgeist on 2007-09-16
Sorry I have not tried network cards bonding up to know, but I intend to do so.
You should have a look at the following tutorial which explains it in details:
[http://www.linuxplanet.com/linuxplanet/tutorials/6414/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6414/1/)

---

