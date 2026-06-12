---
title: "Network setup problems"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by colsandurz on 2007-04-06
I just installed Ubuntu on an older computer and I can't quite figure out how to get the internet connection to work.  I have a cable connection which goes through a linksys WRT54G router (Which I can't access form the computer).   I have a RealTek RTL 8139 ethernet card (wired), I believe it's not a driver as the drivers for this card are in the Linux Kernel.  Here's the realtek site with the driver information.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

Also, the only successful ping I can perform is localhost, everything else is unreachable.


 Here's some commands I ran...

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:40:F4:49:29:BE  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107848 (105.3 KiB)  TX bytes:107848 (105.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

lspci
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)
02:01.0 USB Controller: NEC Corporation USB (rev 41)
02:01.1 USB Controller: NEC Corporation USB (rev 41)
02:01.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:0b.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
02:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
```

lspci -n
```
00:00.0 0600: 8086:2530 (rev 04)
00:01.0 0604: 8086:2532 (rev 04)
00:1e.0 0604: 8086:244e (rev 04)
00:1f.0 0601: 8086:2440 (rev 04)
00:1f.1 0101: 8086:244b (rev 04)
00:1f.2 0c03: 8086:2442 (rev 04)
00:1f.3 0c05: 8086:2443 (rev 04)
00:1f.5 0401: 8086:2445 (rev 04)
01:00.0 0300: 10de:0250 (rev a3)
02:01.0 0c03: 1033:0035 (rev 41)
02:01.1 0c03: 1033:0035 (rev 41)
02:01.2 0c03: 1033:00e0 (rev 02)
02:0a.0 0200: 10ec:8139 (rev 10)
02:0b.0 0401: 1102:0004 (rev 03)
02:0b.1 0980: 1102:7003 (rev 03)
02:0b.2 0c00: 1102:4001

```


cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

Any advice would be appreciated.

---

### Post by Floppyjoe on 2007-04-06
(1) Is the wired interface activated in System/Administration/Networking?
(2) What is the output of :
```
sudo dhclient eth0
```
(3) What version of Ubuntu are you running?

---

### Post by colsandurz on 2007-04-06
(1) I'm not quite sure what you mean... are you asking if it's enabled? Yes, it is enabled.  

(2) sudo dhclient eth0

```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:40:f4:49:29:be
Sending on   LPF/eth0/00:40:f4:49:29:be
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

(3) I'm running 6.10

---

### Post by Floppyjoe on 2007-04-06
Is your router set up for DHCP?

---

### Post by colsandurz on 2007-04-06
Yes, it's "internet connection type" is set to "Automatic Configuration DHCP"

Also, there are two other computers (both running windows XP, one wired, one wireless) on this router.

---

### Post by colsandurz on 2007-04-07
Can anyone help me with this?  Or even tell me where the problem is?  Is the problem with linux or could it be with the ethernet card?  Could it be that my router isn't compatible with linux or that it can't handle windows and linux computers on the network.

---

### Post by Floppyjoe on 2007-04-08
> **colsandurz said:**
> Can anyone help me with this?  Or even tell me where the problem is?  Is the problem with linux or could it be with the ethernet card?  Could it be that my router isn't compatible with linux or that it can't handle windows and linux computers on the network.

Your router is compatible with Linux. The router should be able to handle whatever type of computer OS you have. I am more familiar with wireless problems than wired ethernet problems since there seem to be much more of the wireless variety on the forum. I can't see where the problem is myself but there may be someone with more knowledge of wired interface problems that does.

---

### Post by beauwulf on 2007-04-08
I'm sure there's no compatibility problem with your router - routers are designed to work with internet protocols which are based on old-skool UNIX :)

It seems that your network card is working but your router is not handing out an IP address (DHCP). 
I noticed you said ""internet connection type" is set to "Automatic Configuration DHCP"" but that seems to describe how the router connects to your ISP, rather than how it allows local computers to connect to it. Try looking under "Network Setup" for DHCP Server:  enable / disable. 

If that's not it, I'm out of ideas except for the old fall-back of double checking that everything is plugged in...

---

### Post by Floppyjoe on 2007-04-08
I have added a screenshot which shows the dhcp enable part near the bottom of my screen using a similar router.

---

### Post by colsandurz on 2007-04-08
Well, I looked at the back of my computer and noticed that neither of the two activity LEDs on my ethernet card were lit up.  Thinking that it was possible that something had blown out out on the card I unplugged my computer, took out the card, examined it, realized there was nothing wrong, put it back in, booted my computer and.... my internet connection worked just fine.  I have no idea why this worked and I would be interested to know if anyone could explain it.

---

### Post by Mellon on 2007-04-08
maybe a cable problem, most of the time thats the problem.

---

### Post by tech4me on 2007-04-09
computer@computer-desktop:/$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:21:3c:93:f7
Sending on   LPF/eth0/00:19:21:3c:93:f7
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.23 -- renewal in 36544 seconds.


am facing problem with my card it is diables why ??  i cant :confused:

---

