---
title: "Problem with Atheros when going from XP to Kubuntu"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by nlakes on 2008-11-16
Hi everyone, 

I'm new to Kubuntu, one day exactly, and I'm having a few teething issues.

For some reason, when I go to use XP then come back to Kubuntu I cannot use my wireless internet, and in the network manager I cannot see the ability to connect wirelessly.

Here is what someone got me to do on another topic:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCIController [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-EFast Ethernet Controller [11ab:4352] (rev 14)
0a:03.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bgNIC [168c:001a] (rev 01)
0a:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0a:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]


So does this help you work out what driver I need to install to fix this problem? 
I'm a bit stuck on this one.

Thanks, p.s. I'm loving Kubuntu thus far, it's just a bit complicated to do things - or rather much different than the way i'm use to doing it - I hope it gets easier!

---

### Post by nlakes on 2008-11-16
I've tried disabling it in devices manager, 

reboot

sudo aptitude install linux-backports-modules-intrepid-generic

reboot

to no success... 

any ideas?

Thanks.

---

### Post by acreech on 2008-11-16
I have a an Atheros ar5007eg network card. I am using Ubuntu. I tried the backports souggestion in the past, but was unable to get that to work for me. I did get it to work on my hardy system and again on the intrepid system by following the instructions in my post...... 

[http://ubuntuforums.org/showthread.php?p=6156777#post6156777]("http://ubuntuforums.org/showthread.php?p=6156777#post6156777")

It is post #6.

---

### Post by nlakes on 2008-11-16
> **acreech said:**
> I have a an Atheros ar5007eg network card. I am using Ubuntu. I tried the backports souggestion in the past, but was unable to get that to work for me. I did get it to work on my hardy system and again on the intrepid system by following the instructions in my post...... 

[http://ubuntuforums.org/showthread.php?p=6156777#post6156777]("http://ubuntuforums.org/showthread.php?p=6156777#post6156777")

It is post #6.


Thanks for the help, but it didn't work. 

no such file as wireless_atheros when I tried to download it from the acer site...

---

### Post by nlakes on 2008-11-16
I've downloaded something from atheros called Madwifi, its in my home directory.

Could someone please tell me how to install it?
There is not install file to click on like I'm use to.

Thanks.

---

### Post by nlakes on 2008-11-16
Anyone? Please help, If I can't get this to work - I'm going have to go back to a world of XP only.

---

