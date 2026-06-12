---
title: "Can someone help me get my friend's ubuntu wireless up quick?"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by hlmijendrix on 2008-01-29
I don't really know where to go..it's a different wireless driver than mine and google isn't helping much. Let me know if you need anymore info

```
james@james-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

```

---

### Post by hlmijendrix on 2008-01-29
Here's what I'm seeing if it helps...

[img]http://img227.imageshack.us/img227/5530/screenshotjv2.png[/img]

---

### Post by hlmijendrix on 2008-01-29
Nevermind got it....

---

### Post by SunnyDaze on 2008-01-30
Glad I could be of assistance!!  ;-)

---

### Post by hlmijendrix on 2008-01-30
Uhh...I had it working..all the wireless networks showed up in the network manager and I connected fine...but I restarted it and now no wireless networks show up and there is no wireless option in the network manager.

---

### Post by hlmijendrix on 2008-01-30
bump

---

### Post by rustybronco on 2008-01-30
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

search...bcm4311, here's one to get you started [http://ubuntuforums.org/showpost.php?p=2431305&postcount=1](http://ubuntuforums.org/showpost.php?p=2431305&postcount=1)

---

### Post by Michl on 2008-01-30
You need to edit /etc/network/interfaces and delete everything except these two lines:
```
auto lo
iface lo inet loopback
```

Then reboot.  Network manager has to see the external networks
first and by itself.  The info is available in ubuntu.com documentation.
Remember, there are two network icons up there, one is for
the network manager and the other is the network monitor.  They're
competing now, is my guess.

Michael

---

### Post by jan quark on 2008-01-30
use my guide
i have the same card 4311 broadcom it should work also for you
[http://janquark.fatfreehost.com/tutorial1.html](http://janquark.fatfreehost.com/tutorial1.html)
this is to install the drivers

do you want also to know how to set up the network ips and all?
for instance here is my picture of the manually configured network

---

### Post by hlmijendrix on 2008-01-30
Alright thanks for the help so far

I had it running and I had to restart..once I restarted it...no wireless networks show up once again.

I would like to learn how to set up the network settings...there isn't an option for wireless...just for a wired connection and a modem connection.

---

### Post by NeoGreen on 2008-01-30
Is the wireless NIC enabled or on.  If it isn't on it won't detect.  If this is no a desktop.  Go to your network settings an see if it is enabled.  If this is on a laptop then it may be turned off.

---

### Post by hlmijendrix on 2008-01-30
I'm not sure...here's what I see though...

[img]http://i31.tinypic.com/1zxrwcn.png[/img]

---

