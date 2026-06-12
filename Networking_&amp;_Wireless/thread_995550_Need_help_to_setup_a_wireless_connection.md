---
title: "Need help to setup a wireless connection"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Surendra on 2008-11-27
Hi I installed ubuntu server on my virutal PC. Internet working fine on windows. But in ubuntu i am able to get the internet only on wired. I need to fix the wireless on this. 

I installed ndiswrapper successfully. But still not able to see the wireless connection.

 
ifconfig

[PHP]eth0      Link encap:Ethernet  HWaddr 00:03:ff:6e:80:c9
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:ffff:fe6e:80c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1877 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:251603 (245.7 KB)  TX bytes:164025 (160.1 KB)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:119585 (116.7 KB)  TX bytes:119585 (116.7 KB)

root@ubuntu:~#
[/PHP]



 iwlist scan

[PHP]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

root@ubuntu:~#
[/PHP]





lshw -C network

 [PHP] *-network
       description: Ethernet interface
       product: DECchip 21140 [FasterNet]
       vendor: Digital Equipment Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 20
       serial: 00:03:ff:6e:80:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.110 latency=64 module=tulip multicast=yes
root@ubuntu:~#

[/PHP]




cat /etc/network/interfaces
[PHP]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
root@ubuntu:~#
[/PHP]


Can anybody tell how to fix this problem.

THanks

---

### Post by superprash2003 on 2008-11-28
you need to add the wifi card in the virtual settings for ubntu to recognize

---

