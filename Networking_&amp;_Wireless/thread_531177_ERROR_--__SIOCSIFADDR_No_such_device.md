---
title: "ERROR --  SIOCSIFADDR: No such device"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by professor-g on 2007-08-21
Mini-cluster to do quantum mechanical computations (using MPQC & G03)
Server running 7.04 Feisty Fawn no problems.
Installed 7.04 Feisty Fawn onto 7 slave computational nodes.

Server has eth0 out to net (works fine)
Server has eth1 for internal network to slaves (192.168.2.1)

iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
gateway 192.168.2.1


Failure brigning up eth0 on slave nodes as 192.168.2.XX

my /etc/network/interfaces  on nodes :

auto eth0
iface eth0 inet static
address 192.168.2.14 (for example)
netmask 255.255.255.0
gateway 192.168.2.1


ERROR:
"""""""""
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: no such device
(repeat 3 times, followed by)
Failed to bring up eth1


Heard of potential problem with Ubuntu defining onboard ethernet cards as eth0
Therefore try defining the eth as eth1.
Solved this problem last time doing this, while using older Ubuntu distros - with exact same hardware.
Doesnt work this time.

Please advise.
Thx. 


G.

---
server and 7-node mini cluster of :
Intel Core2 Duo E6420 - 2.13GHz, 1066MHz FSB, 4MB L2
Gigabyte GA-VM900M boards
4 x 1GB DDR II - 667 MHz
7.04 Feisty Fawn server edition

---

### Post by professor-g on 2007-08-21
CORRECTION :

server has ETH1 NOT ETH0 defined for internal network :


auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0
gateway 192.168.2.1

---

