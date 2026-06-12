---
title: "Going Crazy, Can't get wireless working."
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by jrm19852007 on 2008-10-06
Hi, I'm a complete newb at linux and this is the first time I've ever used Ubuntu 8.04. I've gone through forums and searched everywhere on the web and I can't get my wireless card to work. The Wi-Fi light won't even come on.

PC Specs-
Dell E1705
1 GB Ram
Intel Core Duo
Genuine Intel(R) CPU T2250 @1.73GHz
Genuine Intel(R) CPU T2250 @1.73GHz
Hitachi ATA Device 80GB
ATI Mobility Radeon X1400
Broadcom 440x10/100 Intergrated Controller
Broadcom 802.11g Network Adapter

I have bcmwl6.sys broadcom driver installed on Vista Premium.

I'm fairly windows and osx savvy but, I'm just starting with Ubuntu, simplify help please.:)

---

### Post by Ayuthia on 2008-10-06
If you are currently in Ubuntu, can you go into the Terminal and type the following command:
```
lspci -nn
```
Please copy and paste the results.  There are several options for the Broadcom card so it will be helpful to find out which chipset you have so that we can try to provide the best option for you.

---

### Post by jrm19852007 on 2008-10-06
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X1400 [1002:7145]
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

---

### Post by Ayuthia on 2008-10-06
You might start by going to System->Administration->Hardware Drivers.  There should be a listing for Broadcom cards.  You will need to enable it.  Make sure that you have a working internet connection.  That should take care of it for you.  If not, please come back and let us know what happened.

---

### Post by jrm19852007 on 2008-10-06
I went to system >administration >hardware drivers and still got nothing. It says &#8220;No proprietary drivers are in use on this system.  In the window under Component >Device Driver my ATI Accelerated Graphics driver is listed, not in use and if I try to enable it I get W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-18.41_i386.deb)
  Could not resolve 'security.ubuntu.com'
I suppose this is because I can't connect to the net to get the required information downloaded...???
Either way still no wireless connection.
I appreciate the help though. What else you think could be the issue?

---

### Post by Ayuthia on 2008-10-06
> **jrm19852007 said:**
> I went to system >administration >hardware drivers and still got nothing. It says “No proprietary drivers are in use on this system.  In the window under Component >Device Driver my ATI Accelerated Graphics driver is listed, not in use and if I try to enable it I get W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-18.41_i386.deb)
  Could not resolve 'security.ubuntu.com'
I suppose this is because I can't connect to the net to get the required information downloaded...???
Either way still no wireless connection.
I appreciate the help though. What else you think could be the issue?

Well, there are some cases where the 4311 card does not show up there.  You are correct about the error message that you received.  If you don't have a working internet connection in Ubuntu, it will run into this.

Since you are send out a post, I am assuming that you are able to download files somewhere and load them into Ubuntu.  Here is a guide that might help. Just go to Option 2 and you should find instructions on how to get the files you need and get the card working:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

---

### Post by jrm19852007 on 2008-10-06
Thanks, I'll give it a shot and report back.  Im dual booting and keep jumping to other OS to get net access, LOL.

---

### Post by jrm19852007 on 2008-10-08
AWESOME!!! Thanks, I got wireless working with the steps you lead me to. It was different, but not as hard as it looked. THANX!!!

---

