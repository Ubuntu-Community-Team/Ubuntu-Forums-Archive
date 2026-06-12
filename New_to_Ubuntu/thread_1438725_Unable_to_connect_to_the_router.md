---
title: "Unable to connect to the router"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by Sechat on 2010-03-25
I cannot connect to the internet through my wireless connection. I used to have windows vista installed on my laptop and I was able to connect through the router. A friend helped me install linux kubuntu this morning and everything is working perfectly fine except for the wireless connection. The first problem is that i'm using fujitsu siemens  which has a double-button thingy for turning on the wifi, which of course was not working, so I found on the forum how to turn it on. The thing is, even when I turn it on it's still not working. It seems as if it cannot get to the router.
 

 I am connected to the internet now through the same router but with the cable and it's working perfectly fine. It just seems i'm not able to connect to it wirelessly.  I found a similar topic on ubuntu forums but it didn't help me much [HTML]http://ubuntuforums.org/showthread.php?t=1028627 [/HTML]I even tried accessing it through it's IP address but it doesn't want to access it.
 Don't know what else to do.


                                  The router model: air-live  802.11G
 Laptop : Fujitsu Siemens Amilo Li 2727 MS2228


Anybody?

---

### Post by 2hot6ft2 on 2010-03-25
It would be more help to know what wifi adapter you have.
Open a terminal
Applications > Accessories > Terminal
and run

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

---

### Post by Sechat on 2010-03-25
that it?

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 04)

---

### Post by Paddy Landau on 2010-03-25
I don't know that wireless. But if it worked on Windows, then I wonder whether ndiswrapper would help?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[https://launchpad.net/auto-ndiswrapper](https://launchpad.net/auto-ndiswrapper)

It's been a long time since I used it, so you'll have to check the documentation.

---

