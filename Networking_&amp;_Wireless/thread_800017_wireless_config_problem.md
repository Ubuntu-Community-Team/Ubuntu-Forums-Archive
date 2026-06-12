---
title: "wireless config problem"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Furanshisuko on 2008-05-19
Hello,
i have an inspiron 1525 laptop
for some strange reason, i cannot connect wireless.
i checked the hardware had no problem.

when i tried detecting the connections
it only detects the cable ethernet
but no wireless

(i dont understand much of computers) but i think it may be some kinda configuration problem
please 
 i dont want to go back to vista, or xp. 

anyone. please with sugar and cream  on top

---

### Post by Ayuthia on 2008-05-19
> **Furanshisuko said:**
> Hello,
i have an inspiron 1525 laptop
for some strange reason, i cannot connect wireless.
i checked the hardware had no problem.

when i tried detecting the connections
it only detects the cable ethernet
but no wireless

(i dont understand much of computers) but i think it may be some kinda configuration problem
please 
 i dont want to go back to vista, or xp. 

anyone. please with sugar and cream  on top
Can you open up a Terminal session and post the results of lspci -nn?  It will help us figure out what type of wireless card you have.  Thanks!

---

### Post by Furanshisuko on 2008-05-19
okay
this is what i got:


00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

---

### Post by mapes12 on 2008-05-19
This thread may help:

[http://ubuntuforums.org/showthread.php?t=571188&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=571188&highlight=broadcom)

---

### Post by Ayuthia on 2008-05-19
> **Furanshisuko said:**
> 
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

This is your wireless card.  Your card does not seem to work with the native drivers so you will need to install ndiswrapper-common and ndiswrapper-utils-1.9 from Synaptic.  If you can find your wireless drivers for XP it can be used as the driver for ndiswrapper.  The files in XP will need to be bcmwl5.inf, bcmwl5.sys (if you are using 32-bit version of Ubuntu).  If you can't find it, you can check the Dell website for them.  You will need to use XP instead of Vista drivers.

Here is a guide that you can use to help get you going:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Your laptop should not need the fix that is listed in the guide.  My recommendation is to install ndiswrapper-common and ndiswrapper-utils-1.9.  Then find an XP driver to use for it.  From there we can test it out.  Once it is tested, we can get it configured.

---

### Post by Furanshisuko on 2008-05-30
Hi Ayuthia.
well finally i installed the ndiswrapper and i use the ndisgtk for the  GUI installing the bcmwl5.inf and the bcmwl5.sys then i apply ndiswrapper -l and
"bcmwl5 : driver installed" but didn't work, now i look the computer of a classmate and she has the wireless icon in the network-admin even if it's off, but i doesn't  , how can i now if my wireless card is wrong?

thx

---

### Post by Ayuthia on 2008-05-30
> **Furanshisuko said:**
> Hi Ayuthia.
well finally i installed the ndiswrapper and i use the ndisgtk for the  GUI installing the bcmwl5.inf and the bcmwl5.sys then i apply ndiswrapper -l and
"bcmwl5 : driver installed" but didn't work, now i look the computer of a classmate and she has the wireless icon in the network-admin even if it's off, but i doesn't  , how can i now if my wireless card is wrong?

thx

If ndiswrapper -l does not show hardware present, then it means that it does not like the driver.  You might try this link also.  The poster has the same card as you:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

---

