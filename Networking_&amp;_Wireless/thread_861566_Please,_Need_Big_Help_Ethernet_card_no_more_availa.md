---
title: "Please, Need Big Help: Ethernet card no more available"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by zenacim on 2008-07-16
hi,

i use ubuntu 8.04 32bits


i m a student and i have to finish my thesis in one month.

i moved in my friend's house to study

i installed an usb wifi stick and it worked not really fne.
so i bought a rj45 cable to use internet

today i test it and the green led of my ethernet card is down

i dont know why, maybe yesterday i had an automatic update of the kernel

that s the infos i have :

ifconfig -a  : 

eth0 Link encap:Ethernet HWaddr 00:16:17:b2:84:65
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       Packets recus:0 erreurs:0 :0 overruns:0 carrier:0
       collisions:0 lg file transmission:1000
       octets recus: 0 (O.O B) octets transmis:0 (0.0 B)
       Interruption: 18 adresse de base:0x600

 ethtool -i eth0  :
driver: forcedeth
version: 0.61
firmware version:
bus-info: 0000:00:14.0

i tried itinerant mode, dhcp and static ip, no result.

the "eth0" disappear from the /etc/network/interfaces


sudo /etc/init.d/networking restart :

Reconfiguring network interfaces
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface atho=ath0.


dmesg grep eth0 j obtiens :

forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:16:17:b2:84:65
eth0: no link during initialization
ADDRCONF (NETDEV_UO) eth0: link is not ready




Please, what can i do ???

i tested a live cd of 7.04 but same result

---

