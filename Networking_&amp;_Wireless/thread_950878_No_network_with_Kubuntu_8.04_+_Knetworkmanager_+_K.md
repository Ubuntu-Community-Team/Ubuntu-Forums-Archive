---
title: "No network with Kubuntu 8.04 + Knetworkmanager + Kde4"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by falkenberg_cph on 2008-10-17
Hi
I just did a fresh install of Kubuntu Hardy Heron with Kde4 today. It is on a dual boot with XP. I cannot get any Wired network working. I have been searching for hours for a solution.

Now I'm  hoping some of you can help me find the problem.

Btw: I thought it might have something to do with Kde4 so i was gonna install 8.04 with kde3 instead. The live CD with Hardy + Kde3 had the same problem.

Appreciate all help available
Thanks
Carsten

[EDIT]:
This thread is much like my problem. Not solved:
[http://ubuntuforums.org/showthread.php?t=437687&page=3](http://ubuntuforums.org/showthread.php?t=437687&page=3)

---

### Post by falkenberg_cph on 2008-10-18
I hope some more information can help you help me :)

First of all: How is networking handled in Kubuntu Hardy? And has it changed with KDE4? I read in some thread that knetworkmanager did not use /etc/network/interfaces any longer. I am also almost sure that there was no /etc/resolv.conf when i first installed Kubuntu.

I use a router and i know from other computers that both wired and wireless is working with Ubuntu and XP. (One of those computers is this one).

Here is a bunch of diagnostics:

ping:
```
ping www.google.com
ping: unknown host www.google.com

```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:13:3d:82
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:12699 (12.4 KB)
          Interrupt:3 Base address:0x2000

eth0:avahi Link encap:Ethernet  HWaddr 00:03:0d:13:3d:82
          inet addr:169.254.3.213  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1744 (1.7 KB)  TX bytes:1744 (1.7 KB)

```

lspci:
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:03.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
01:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
01:0c.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

```

sudo route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```

cat /etc/resolv.conf
Gives no result (The files is empty).

cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback

```

---

### Post by dasacc22 on 2008-10-27
hey, your wired interface didn't contact the dhcp server for an addy. Try running

$> dhclient eth0

and see what turns up. Could be a physical problem with the cable or whatever. Just make sure you have blinky lights on the router and on your eth card.

---

