---
title: "I just did todays update, and my wireless card stopped working!"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by twang103 on 2008-05-04
I just did the daily update on my HP pavilion dv6019 running 8.04.
My wireless card is no longer recognized after the update, however my wired connection still works. when i go to network settings, only the wired connection is listed...
Any ideas how to fix it?

---

### Post by Paris Heng on 2008-05-04
> **twang103 said:**
> I just did the daily update on my HP pavilion dv6019 running 8.04.
My wireless card is no longer recognized after the update, however my wired connection still works. when i go to network settings, only the wired connection is listed...
Any ideas how to fix it?

I think this is the hardware issue, try search some firmware for your card. Honestly, i never encounter this kind of problems yet.

---

### Post by backdoc on 2008-05-04
> **twang103 said:**
> I just did the daily update on my HP pavilion dv6019 running 8.04.
My wireless card is no longer recognized after the update, however my wired connection still works. when i go to network settings, only the wired connection is listed...
Any ideas how to fix it?

I am having troubles, too.  I had it working with the ndiswrapper just fine before upgrading.  Now, there appears to be some conflict with an ssb module.  I have a pretty decent understanding of how it all works.  I just can't seem to make it happen.  Anyway, while my reply may not be exactly what you need, I thought it might point you in the right direction or, help someone else.

I have an older dell laptop with the Broadcom wireless chip.  It's the True Mobile 1300 which uses the bcmwl5.inf driver.

To me, step one is to get the hardware recognized.  Type iwconfig without any options and see if your wireless card shows up.  If it does, you probably just need to configure it.  If not, your drivers are still a problem.  That's where I am right now.  After you get your card to show up, I find that configuring it manually with iwconfig takes a layer of complexity out.  If you can set it up with iwconfig, you can work to automate afterwards.  If not, you still have to figure out why.  Let's say you can get it to connect by manually configuring it with iwconfig, to automate it, edit the /etc/network/interfaces file to set it up.  Once you have that configured, you can use ifup and ifdown to bring your network adapter up/down.  It works with the interfaces file.

These are the broad essential steps.  I find it helpful to look at things in large general steps.  

To load drivers for your hardware, use modprobe.  To remove them, use rmmod.  To see them, use lsmod.  To see what resources your card is using, use lspci.  When listing things, it is often helpful to pipe your results through grep.  I use the "-i" option with grep to make it case insensitive.  Here's an example or two:

lsmod | grep -i ndiswrapper
lspci | grep -i broadcom

Oh, and to prevent modules from loading, you blacklist them by adding them to the list of blacklisted modules in /etc/modprobe.d/blacklist.

The problem I am having right now is step one.  It was working fine with Gutsy.  The upgrade broke it.  I'm not sure, but I think ndiswrapper has changed.

---

### Post by Ayuthia on 2008-05-04
twang103-Can you post the results for the following:
```
lspci -nn
lsmod|grep -i -e b43 -e bcm43xx -e ndiswrapper -e ssb
```

backdoc-Check out this section:[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c)
It gives you some options on how to load ndiswrapper before ssb.

---

### Post by twang103 on 2008-05-05
msbe188@HP-Pavilion:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
07:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
07:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
msbe188@HP-Pavilion:~$ lsmod|grep -i -e b43 -e bcm43xx -e ndiswrapper -e ssb
msbe188@HP-Pavilion:~$

---

