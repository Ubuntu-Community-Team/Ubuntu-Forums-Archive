---
title: "New to Ubuntu - Need help troubleshooting wireless"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by wyman on 2007-08-21
I am new to Ubuntu, and I recently installed Ubuntu (FF) on an old computer and have a wireless card (Belkin F5D7000 ver 6000) I would prefer to use. When I turn the box on, I can see and "connect" to the network, but it still acts as though I am not connected (i.e., can't connect to internet, etc.). Everything works through a wired connection, but wireless is useless at this point. I have tried several things that I have searched for on the forums and they have not worked for me, requiring me to have to do a reinstall of the entire OS.

If there are no solutions for this problem, can anyone recommend a distro that this card will work on for sure?

Thanks for taking the time to read this.

---

### Post by moore.bryan on 2007-08-21
*what's the output of ```
lspci
``` and ```
iwconfig
```?  that'll give us more information about your card...*

---

### Post by nosrednaekim on 2007-08-21
try a quick ping of 192.168.0.1 or 192.168.1.1 (your router) by running "ping 192.168.1.1" or 192.168.0.1

that will tell you if it is a problem with the internet specifically or your connection

if it can't ping wither of those two addresses, its a problem with your wireless connection

---

### Post by wyman on 2007-08-25
Sorry for the late reply, I have been very busy this past week.
[quote="lspci"]00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:02.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:02.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 05)
00:12.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 64)
00:14.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:01.0 VGA compatible controller: S3 Inc. Trio 64 3D (rev 01)
[/quote]

[quote="iwconfig"]lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"Rife"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:2D:47:7A   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=97/100  Signal level:-44 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/quote]

When I attempt to ping my router, I get a "Network is unreachable" message.

---

### Post by kevdog on 2007-08-25
Just some humble advice --

Please see following thread -- its about the rt73 driver.  You are using the rt61 driver.  Read the post about 3 times before doing anything and then when you understand what you are doing, just substitute 61 everywhere 73 is listed.  It is the exact same process, the only difference is that you are using the rt61 driver rather than the rt73 driver.

Here is the linki:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

Post back if you have questions.

---

### Post by wyman on 2007-08-25
I think I got everything working, thanks.

---

### Post by moore.bryan on 2007-08-25
*excellent; glad to hear it.*

---

