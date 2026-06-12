---
title: "Lost wired ethernet (DNS) after uprgrade from 16.04 to 17.1  Dell 745 Broadcom card"
date: 2018-04-21
forum: Networking &amp; Wireless
---

### Post by elecmail on 2018-04-21
Not adept at this so looking for newbie level help - Recently upgraded from good 16.04 to 17.1 on Dell 745 with Broadcom BCM5754 card. Ethernet is connected but cannot access either for Ubuntu release site or Firefox. Dual boot system and W7.0 still works as does 16.04 when run from DVD. Shows connected at 100 mbps. Can ping router and 8.8.8.8 but not google.com so is a DNS issue. Using tg3 kernel same as before. Here is some setup info:

mitch@optiplex745:~$ sudo cat /etc/lsb-release; uname -a
[sudo] password for mitch: 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"
Linux optiplex745 4.13.0-38-generic #43-Ubuntu SMP Wed Mar 14 15:20:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

mitch@optiplex745:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Limited NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
    Subsystem: Dell OptiPlex 745 [1028:01da]
    Kernel driver in use: tg3

mitch@optiplex745:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gateway         0.0.0.0         UG    20100  0        0 eth0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0
mitch@optiplex745:~$ 

mitch@optiplex745:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

mitch@optiplex745:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 059b:0252 Iomega Corp. Optical
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

mitch@optiplex745:~$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.13  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::6391:5539:66db:11c  prefixlen 64  scopeid 0x20<link>
        ether 00:1a:a0:be:b3:e4  txqueuelen 1000  (Ethernet)
        RX packets 1336  bytes 379247 (379.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 467  bytes 71638 (71.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5850  bytes 379260 (379.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5850  bytes 379260 (379.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

Any ideas?  thx

---

