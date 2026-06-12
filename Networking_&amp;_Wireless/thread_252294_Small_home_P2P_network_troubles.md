---
title: "Small home P2P network troubles"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by ashughes on 2006-09-06
Ok, this is what I want to do:

Ubuntu PC
---------
Eth0: DHCP, connects to dorm network for internet
Eth1: Static, connects to laptop via crossover

WinXP Laptop
------------
Eth0: Static, connects to PC via crossover

I want them to be able to share resources and the internet connection.

Here is my current IP configurations:
(IP/Subnet/Gateway)

PC.Eth0: DHCP (192.168.1.101/255.255.255.0/192.168.1.1)
PC.Eth1: Static (192.168.0.1/255.255.255.0/192.168.1.101)
Laptop.Eth0: Static (192.168.0.2/255.255.255.0/192.168.0.1)

From the PC, I can do anything.  The laptop however gets to PC.Eth0 then hits a wall.  I can ping 1.101 with it, but not 1.1.

If it helps, I have included a small diagram of what I want:

|
|          
|<--patch--> Eth0 Eth1 <---crossover---> Eth0
|

Any help here would be great.  Hell, if you wanna tell me exactly what configuration numbers I need, go right ahead.

Basically what I am trying to do is set up my desktop as a webserver and then use my laptop as my everyday computer.

Thanks.

---

