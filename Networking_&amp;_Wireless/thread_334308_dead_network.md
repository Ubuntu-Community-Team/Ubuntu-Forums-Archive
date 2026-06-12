---
title: "dead network"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by googlethis on 2007-01-08
hi,
I'm new to Linux, so i have no idea where to even start. i can't get any response from my network. i tried to change the network settings through the system->administration->networking to custom settings that i know work. i know the hardware works, at least with windows. please help.

---

### Post by googlethis on 2007-01-08
also i should probably say that I'm running 6.10.

---

### Post by phossal on 2007-01-08
Networking problems aren't easy to solve with no information, so here are the basics: You're going to post the output from each of the following commands, tell us what your hardware is, and indicate whether your interfaces are wireless or not.

```

sudo ifconfig
sudo iwconfig
sudo lspci
sudo lsusb
```

If you're using a router, any wep/wpa should be off, dhcp should be *on*, and you should avoid configuring too many files, or using too many GUI tools. In fact, my personal preference is to *avoid the GUI tools and the configuration files until it's confirmed that the hardware is properly recognized and connected.*

---

### Post by Jussi Kukkonen on 2007-01-08
Post some info on your hardware and network (wlan or wired, are there any lights on the card, what models are the cards, etc. ).

output of the following commands may also help:
```
cat /etc/network/interfaces
ifconfig
dmesg | grep eth
```

---

### Post by googlethis on 2007-01-08
wow that was alot faster of a response than i expected. i'll upload those terminal responses in a moment. i have to move around to a computer with working internet.

---

### Post by googlethis on 2007-01-08
my hardware is as follows.
AMD Athalon64 2800+ processor
1024 MB RAM
80GB HDD
256MB nVidia fx5700LE graphics card

This is the ethernet controller. it's integrated into the motherboard, so there aren't any lights
VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

it's a wired network BTW.

Here are the terminal outputs.


faceboy@facebox:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:50:70:E8:3B:C8  
          inet6 addr: fe80::250:70ff:fee8:3bc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4572 (4.4 KiB)
          Interrupt:185 Base address:0xed00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)


faceboy@facebox:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


faceboy@facebox:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)


faceboy@facebox:~$ sudo lsusb
Bus 005 Device 006: ID 05ac:1209 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:0053 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c512 Logitech, Inc. 
Bus 001 Device 005: ID 03f0:4d11 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000

---

### Post by googlethis on 2007-01-08
those smiley faces are in there because 8 ) turns it into one. i cant get them out but it just says: "(rev 78 )" on both

---

### Post by googlethis on 2007-01-08
the other two codes i was given by Jussi Kukkonen are:
faceboy@facebox:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

faceboy@facebox:~$ dmesg | grep eth
[17179585.544000] eth0: VIA Rhine II at 0x1ed00, 00:50:70:e8:3b:c8, IRQ 185.
[17179585.548000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[17179586.556000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179628.936000] eth0: no IPv6 routers present

---

### Post by cuonght on 2007-01-08
I also found my network dead. I am using laptop. When I am moving from my dorm to office, where there are different IP address, I could not use internet. Please help!

---

### Post by Jussi Kukkonen on 2007-01-09
Well, the device is detected and seems to be working (in fact I have the same model working fine here).

You don't seem to have an IP address though (and it's set on DHCP, not a custom IP setting). Should you be using a specific IP address or is dhcp (a dynamic IP received from a router, modem or server) available? 

cuonght, start a new thread for your issue -- this one is for dicussing this specific problem.

---

### Post by kazuya on 2007-01-09
got the same issue yesterday. If I am successful I would post back what I did. I am using Edgy though. Not a laptop, a home wired desktop PC.

---

### Post by repins on 2007-01-09
I am having the same issue too. I only have internet access for about a minute or so, and the only way to get a connection again is to power cycle my modem and renew my ip.

---

### Post by kazuya on 2007-01-09
do we have to escallate this to the devs? Are you using dapper, edgy, or fiesty? Thanks though for the tip on power cycling the router, and modem. Simply restarting the PC does not help.

---

### Post by repins on 2007-01-09
dapper drake and here is my output

          collisions:0 txqueuelen:0
          RX bytes:872 (872.0 b)  TX bytes:872 (872.0 b)


dorian@dozer:~$ sudo iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.



dorian@dozer:~$ sudo lspci
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
0000:02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:02:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:02:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
0000:02:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

dorian@dozer:~$ sudo lsusb
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000


dorian@dozer:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:a1:08:39:31
Sending on   LPF/eth0/00:08:a1:08:39:31
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 64.59.176.40 port 67

################

also when i do **sudo ifup eth0** it just hangs there, sending request's. The only way i can get back online for a minute is by deactivating eth0 , power cycling  my modem, waiting till it gets online, then activating eth0 again. The really weird thing about this is that it is a fresh install, and i have installed it before on the same box, and i did not have this issue.

Any help?

---

### Post by googlethis on 2007-01-09
Just an fyi: im using edgy.

---

### Post by googlethis on 2007-01-10
i got it working, i don't know how but i did it. the only thing is that everything is running slower than dial up, but I'll start a new forum for that

---

### Post by repins on 2007-01-10
YAY.... i found the soloution to my problem.. This has to do with my nic (cnet pro200wl), and appernetly from what i understand the tulip driver was interfering with the cnet???
[COLOR="Red"]
$sudo modprobe -r tulip

$sudo modprobe -r dmfe

$sudo modprobe dmfe[/COLOR]



And i have internet again..

---

