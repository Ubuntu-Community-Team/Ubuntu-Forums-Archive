---
title: "Ethernet cards incorrectly recognised"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by eugenia on 2006-09-02
I have 2 dual boot Ubuntu/Win desktops.

The desktop I was using as a 'server' had a motherboard fault (the case speaker would not work which was a hassle with VoIP as I couldn't hear it ring) so I thought I would be smart and swap cases - and therefore motherboards - by merely by putting the hard disks from one into the other.

This has caused me more grief than I expected, however, I am slowly solving the problems and learning more. One of the issues was the Xserver had to be reconfigured and I won't mention the problems this has caused Windows.  

This 'server' desktop has 2 RJ-45 connections, 1 onboard (HWaddr 00:11:D8:B5:37:1F) and one in the PCI slot (HWaddr 00:30:BD:18:EB:BF).

For some reason Ubuntu 5.10 is now coming up with the following.

eth0      Link encap:Ethernet  HWaddr 00:30:BD:18:EB:BF
          inet6 addr: fe80::230:bdff:fe18:ebbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:13068 (12.7 KiB)
          Interrupt:18 Base address:0xe400

eth2      Link encap:Ethernet  HWaddr 00:11:D8:B5:37:1F
          inet addr:203.87.58.176  Bcast:203.87.58.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feb5:371f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:114228 (111.5 KiB)  TX bytes:39996 (39.0 KiB)
          Interrupt:19 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1850799 (1.7 MiB)  TX bytes:1850799 (1.7 MiB)

Can anyone suggest how to make Ubuntu recognise the onboard connection (HWaddr 00:11:D8:B5:37:1F) as eth0 and the PCI card (HWaddr 00:30:BD:18:EB:BF) as eth1 and get rid of the spurious eth2.

System > Administration > Networking is no help as it has a mind of its own. I even deleted /etc/network/interfaces but it didn't fix it.
A search of the forums and Google have been fruitless to date.

My ADSL modem is physically connected to the onboard RJ-45 and shows the correct MAC 00:11:D8:B5:37:1F.

---

### Post by eugenia on 2006-09-06
The answer is in the file /etc/iftab (as far as I can see one of those undocumented features of Ubuntu that needs to be documented somehow)

---

