---
title: "nvidia MCP61 ethernet card problem with (k)ubuntu"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by fb314 on 2007-12-20
Hi,

I have built a PC based on a Gigabyte GA-M52S-S3P (NVIDIA GeForce 6100 + NVIDIA nForce 430) motherboard, and a AMD athlon 64x2.
I successfully installed kubuntu 07.10 (AMD64 version) and, during the update processing (there were 64 updates available), the wired network suddenly went out. Even after rebooting, the network doesn't show up anymore.
I'm on a lan where there is a DHCPD serveur. Whether I let the automatic conf or I manually configure it, the result is the same.
I have test with another identical PC, again with the same result: the problem is software, not hardware.

here's some infos:

lshw
```
description: Ethernet interface
product: MCP61 Ethernet
vendor: nVidia Corporation
logical name: eth0
```

ethtool -i eth0
```
driver: forcedeth
version: 0.60
```

ethtool -t eth0
```
The test result is FAIL
```

I have tried to unload/reload the forcedeth module, with no success. Indeed, even a reboot does nothing.

My conclusion is that the network software has been broken by the new (official !) updates since the 07.10 release.

Any idea ?

---

### Post by lukeminus on 2007-12-22
I am in the same boat, if anyone has any ideas HElP!... please :)

---

### Post by 8rino on 2008-01-03
Hi, 
so we can say that we are "three men in a boat" !! 
I'm using gnome instead that Kubuntu

eth0 has benn working flawlessly for more than one month, but yesterday suddenly refused to be configured by the DHCP server. And it do not accept a manual reconfiguration by ifconfig command.

I do not know how to solve the problem, but I've done the following

1) I started the system with the install DVD (downloaded and installed on nov 29 2007.
The aim was to see that it was a software (some upgrade?) or hardware problem. 
It resulted in the same problem. 
The card was not configured and do not accept the IP number with
ifconfig eth0 192.168.8.57

2) I shutted down the system and installed a RealTek RTL8139 card. At first boot it was not recognized by the system, but it was at the second boot. The DHCP server gave the IP number to the Realtek and I was back in business.

3) At this point I tried to reconfigure eth0 with 
ifconfig eth0 192.168.8.57
successfully, but when I removed the patch cord from eth1 (Realtek) to plug it in eth0, I've lost the configuration of both the cards

Hope this helps

Ottorino

---

### Post by Darkchef on 2008-04-01
This isnt good news ive been considering buying this for my new gigabyte motherboard, has this been solved yet ??

---

