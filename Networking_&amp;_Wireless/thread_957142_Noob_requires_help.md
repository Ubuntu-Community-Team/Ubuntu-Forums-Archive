---
title: "Noob requires help"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by tpybear on 2008-10-24
Hi there, just installed ubuntu, and attempted to try to connect wireless to my router. 

buntu@ubuntu:~$ lspci

ubuntu@ubuntu:~$ lspci
00:00.0 
Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 
PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 
USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 
USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 
USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0
SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 
IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 
ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 
PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 
Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 
Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 
VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g 
Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 
FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 
Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

please guide me along, thanks.

---

### Post by melojo on 2008-10-24
[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)
This may help

---

### Post by melojo on 2008-10-24
another link ubuntu documentation 8.04
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)

---

### Post by tpybear on 2008-10-24
Hmm, i can't find "Hardware Drivers". It is not listed under my Adminstration there. Any idea why?

---

### Post by tpybear on 2008-10-24
error: invalid operands to binary &
fwcutter.c:699: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:702: warning: implicit declaration of function ‘extract_or_identify’
fwcutter.c:702: error: ‘const struct file’ has no member named ‘flags’
make: *** [fwcutter.o] Error 1

Also, i have some prob installing b43-fwcutter_011.orig.tar.gz. 
After i "make install", error is reported. Hmm, any help pls?
Thanks alot.

---

### Post by tpybear on 2008-10-25
anyone can help?

---

