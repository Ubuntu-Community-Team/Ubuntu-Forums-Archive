---
title: "[SOLVED] VIA-Rhine VT6102 onboard no internet connection"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by 73ckn797 on 2008-10-04
VIA-Rhine VT6102 on-board no internet connection:

Mobo = ASUS A7V400-MX, AMD Sempron 2400+, 512 memory

System recognizes on-board LAN but cannot connect to internet. Installed a Broadcom NIC card and can connect. Was wondering if on-board LAN is bad or is there a fix? Searching forums found no solution. Have reset router and broadband modem. New Ubuntu Hardy Heron installation for neighbors box.

Terminal information:

 sudo lshw -C network 
*-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:11:d8:28:ac:ca
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:d8:28:ac:ca  
          inet6 addr: fe80::211:d8ff:fe28:acca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6870 (6.7 KB)
          Interrupt:23 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:11:d8:28:ac:ca  
          inet addr:169.254.8.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60868 (59.4 KB)  TX bytes:60868 (59.4 KB)

I have tried several grub menu.lst additions recommeded in other threads (acpi=noirq & irqpoll) which did not help.

Automatic dhcp enabled in Network Manager.

Any ideas?

---

### Post by 73ckn797 on 2008-10-06
Not solved, there was no response.

Reposted info under new title:
[http://ubuntuforums.org/showthread.php?t=937881](http://ubuntuforums.org/showthread.php?t=937881)

---

