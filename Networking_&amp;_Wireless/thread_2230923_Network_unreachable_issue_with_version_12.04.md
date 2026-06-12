---
title: "Network unreachable issue with version 12.04"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by contacts-massonsebastien on 2014-06-22
Hi there!

The issue I'm describing here is ennoying me from a while now (around 6 months factually) and finally decided to end with it.

Before the issue, everything worked fine and I was connected to my LAN using the wired interface eth0.

The issue appeared suddently when I erased VPN connection I don't need anymore.
The eth0 interface juste stopped working.

I suspect that I forgot to change some settings but ... which ones?!
I erased the LAN setting via the X interface to make a new one.  No success.

Since that day, when I'm pinging any thing, as well as my local router, I get the message "Network unreachable".

_**I. investigations:**_
_a) From gnome:_
"_*System settings > Network*_"
A window prompt : "Network services are not compatible with this version (translated on my own, I'm using X in French : "Les services réseau du système ne sont pas compatibles avec cette version")

I then click "Close".
Within the Network window > "_*Wired  connection*_"
The LAN is marked as "Unmanaged" (trans.: "Non-géré")

_b) Command line:_
Ubuntu version I'm using.  **lsb_reslease -a**
```

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

```

Kernetl version.** uname -r**
```
3.2.0-58-generic
```

Devices.
**ip link show**
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether f0:bf:97:18:f8:3c brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 8c:a9:82:44:2c:64 brd ff:ff:ff:ff:ff:ff

```

**lshw -C network**
```

  *-network
       description: Interface réseau sans fil
       produit: Centrino Wireless-N 1000 [Condor Peak]
       fabriquant: Intel Corporation
       identifiant matériel: 0
       information bus: pci@0000:02:00.0
       nom logique: wlan0
       version: 00
       numéro de série: 8c:a9:82:44:2c:64
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-58-generic firmware=39.31.5.1 build 35138 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       ressources: irq:49 mémoire:c7400000-c7401fff
  *-network
       description: Ethernet interface
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:05:00.0
       nom logique: eth0
       version: 06
       numéro de série: f0:bf:97:18:f8:3c
       taille: 10Mbit/s
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       ressources: irq:47 portE/S:3000(taille=256) mémoire:c3404000-c3404fff mémoire:c3400000-c3403fff

```

**lspci**
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```

Wired interfaces.  **cat /etc/network/interfaces**
```

#This file describes the network interfaces available on your system
#and how to activate them.  For more information, see interfaces(5)

#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet dhcp

```

Network settings.  **ifconfig -a**
```

eth0      Link encap:Ethernet  HWaddr f0:bf:97:18:f8:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:47 Adresse de base:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr f0:bf:97:18:f8:3c  
          inet adr:169.254.8.66  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interruption:47 Adresse de base:0x2000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1328 erreurs:0 :0 overruns:0 frame:0
          TX packets:1328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:133217 (133.2 KB) Octets transmis:133217 (133.2 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:44:2c:64  
          inet adr:192.168.1.3  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::8ea9:82ff:fe44:2c64/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:499206 erreurs:0 :0 overruns:0 frame:0
          TX packets:959072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:73572155 (73.5 MB) Octets transmis:1424288046 (1.4 GB)

```

And finally I didn't found any information about the network interfaces with **dmidecode**.


**_II. Solving attemps:_**
I tried to set a static IP address by editing /etc/network/interfaces ... no success.

Restarting network interfaces.  **sudo /etc/init.d/networking restart**
```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.

```

Network routing table.  **route**
```

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
default         *               0.0.0.0         U     1002   0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0

```

Network setting.  **ifconfig -a**
```

eth0      Link encap:Ethernet  HWaddr f0:bf:97:18:f8:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:47 Adresse de base:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr f0:bf:97:18:f8:3c  
          inet adr:169.254.8.66  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interruption:47 Adresse de base:0x2000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1562 erreurs:0 :0 overruns:0 frame:0
          TX packets:1562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:177365 (177.3 KB) Octets transmis:177365 (177.3 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:44:2c:64  
          inet adr:192.168.1.3  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::8ea9:82ff:fe44:2c64/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:690866 erreurs:0 :0 overruns:0 frame:0
          TX packets:1336268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:93022066 (93.0 MB) Octets transmis:1983373695 (1.9 GB)

```

**_III.  Future ..._**
I downloaded latest ubuntu version 14.04 hoping this will solve the issue.  (wait and see ...)

By the way, I wish to learn something new and so to understand where the issue I'm meeting stands.

So!  Can someone help me to find the reason of the issue?


I really thank you for your help.

Rgards,
Sebastien.

---

### Post by contacts-massonsebastien on 2014-06-22
Hello, again!

I installed ubuntu 14.04 over previous version as a new fresh install (not an update).
Same issue.  It doesn't fixed it.

A searched the web for solving the problem with no success.  It seems the "Network unreachable" issue is quite common but others' issues description are always partially the same as the one I'm meeting, never totaly.

I forgot to precise : I'm using a **Sony Vaio** laptop computer.

I thank you for your help,
Regards,
Sebastien

---

