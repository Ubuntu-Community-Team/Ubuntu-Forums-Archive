---
title: "LAN connection not working on Ubuntu ( but works on Windows)"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by peutch on 2007-06-06
Hi guys !

I don't exactly know why, but my wired connection to the university LAN has stopped working under Ubuntu Edgy Eft. But the weird thing is: it still works under Win XP, so I'm a bit confused. I've asked on another Ubuntu forum but noone has found the answer yet. I thought you guys might tell me what you think. I'll post as much information as possible :

sudo ifconfig
```
patrick@patrick-laptop:~$ sudo ifconfig
eth0      Lien encap:Ethernet  HWaddr AA:00:04:00:0A:04  
          inet adr:158.143.184.65  Bcast:158.143.187.255  Masque:255.255.252.0
          adr inet6: fe80::a800:4ff:fe00:a04/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:285 erreurs:0 :0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:39011 (38.0 KiB) Octets transmis:10726 (10.4 KiB)
          Interruption:11 

eth1      Lien encap:Ethernet  HWaddr AA:00:04:00:0A:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:5 Adresse de base:0xc000 Mémoire:fafef000-fafeffff 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:25 erreurs:0 :0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:928 (928.0 b) Octets transmis:928 (928.0 b)
```

lspci
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
```

sudo lshw -C network

```
*-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: aa:00:04:00:0a:04
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5702-v2.25 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:faff0000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 04
       serial: aa:00:04:00:0a:04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 link=no multicast=yes wireless=unassociated
       resources: iomemory:fafef000-fafeffff irq:5
```

cat  /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

A few pings :

```
patrick@patrick-laptop:~$ ping -c6 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5011ms

patrick@patrick-laptop:~$ ping -c6 www.google.com
PING www.l.google.com (66.249.93.147) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5009ms

patrick@patrick-laptop:~$ ping -c6 64.233.169.103
PING 64.233.169.103 (64.233.169.103) 56(84) bytes of data.

--- 64.233.169.103 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 4999ms

patrick@patrick-laptop:~$ ping -c6 158.143.184.1 (MY GATEWAY)
connect: Network is unreachable

patrick@patrick-laptop:~$ ping -c6 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.040 ms

--- 127.0.0.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4998ms
rtt min/avg/max/mdev = 0.037/0.039/0.041/0.001 ms

patrick@patrick-laptop:~$ ping -c6 158.143.184.65
connect: Network is unreachable

patrick@patrick-laptop:~$ ping -c6 158.143.184.1
connect: Network is unreachable

patrick@patrick-laptop:~$ ping -c6 194.2.0.20
connect: Network is unreachable

patrick@patrick-laptop:~$ ping -c6 www.google.fr
connect: Network is unreachable

```

sudo iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

I totally do not understand... Any idea ?

Thank you guys !

---

### Post by homunq on 2007-07-03
I'm having a similar problem on Feisty. I'm still investigating...

---

### Post by Denys on 2007-11-06
Note, that you have same MAC on both interfaces. It seems to be a famous udev eth naming problem.
You need to edit /etc/udev/rules.d/70_persistent-net.rules and set names for interfaces manually. Example:

SUBSYSTEM=="net", DRIVERS=="?*", SYSFS{address}=="AA:00:04:00:0A:04", NAME="eth0"

---

