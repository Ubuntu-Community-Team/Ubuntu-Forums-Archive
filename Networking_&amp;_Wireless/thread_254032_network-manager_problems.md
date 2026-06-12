---
title: "network-manager problems"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by fiacca on 2006-09-09
Good day all, Ibeg you pardon for my lenghty post, but I have trying to solve the problm for a few days ... and I failed.

My hardware is an Asus W5f laptop which is working wery well with Dapper, the only real problem I have is the impossibility to use network manager not only to switch wirelesses, but even to connect to one of them ](*,) .
If I use the network settings program and configure manually the eth1 interface as follows everything works fine:

Network name (ESSID) terminalgolfo
Key Type: Hexadecimal
Wep Key: xxxx

Configuration Static IP address
IP address 172.16.185.26
Subnet mask 255.255.255.0
Gateway address: 172.16.185.254

In order to avoid reconfiguring everytime I change location I installed network manager; first it was unable to detect the network, but after reading the wiki I edited the interfaces file commenting everything except the loopback lines.

After rebooting network manager was able to detect the network but I tried to access the network and no combinations of parameters worked.

Any suggestion? Where am I supposed to put the static ip details?

thanks all

---

