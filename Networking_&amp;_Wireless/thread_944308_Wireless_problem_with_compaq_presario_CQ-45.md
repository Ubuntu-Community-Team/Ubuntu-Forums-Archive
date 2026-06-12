---
title: "Wireless problem with compaq presario CQ-45"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by hmarkg on 2008-10-11
Presario CQ45-129TX
Intel Core 2 duo processor P8600 (2.4GHz)
250GB Hard Disk 
3GB RAM
nVidia GeForce 9200M GS with 256MB DDR2 RAM
Intel WiFi link 5100 network.

I know there are already many other threads about this topic, I've tried to follow the thread from [[http://ubuntuforums.org/showthread.php?t=879134&highlight=intel+wifi+link]](http://ubuntuforums.org/showthread.php?t=879134&highlight=intel+wifi+link]) but still cant get the wifi card to work. 


This is the output when i input iwconfig in terminal

[B]mark@Compaq-CQ45:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/B]

This is the output when i input lspci in terminal

[B]mark@Compaq-CQ45:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e8 (rev a1)
04:00.0 Network controller: Intel Corporation Unknown device 4237
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
06:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
06:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
06:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384[/B]

This is the output when i input ndiswrapper -l in terminal

[B]mark@Compaq-CQ45:~$ ndiswrapper -l
netw5v32 : driver installed
	device (8086:4237) present[/B]

So far I've manage to solve the LCD dimming problem and the display problem. But Wifi and the Sound problem is not solved yet. But in this thread I would wish to solve the wireless problem first and later on the sound.

Help Me...!!! What should I do next.
Many Thanks in advance... :)

---

### Post by sunnsi on 2008-10-14
After I update to 8.10. The wireless network is OK then.
My laptop is CQ45-124TX.
So I suggest you to update your system.

---

### Post by hmarkg on 2008-10-14
Ubuntu 8.10 huh... Ok.. Thank you for helping... what about the sound? Do you have any sound problem?

---

### Post by hmarkg on 2008-10-15
I think i shell wait for the new ubuntu 8.10 version to come out in 15 days time... Teehee...

---

### Post by sunnsi on 2008-10-17
Yes, Here is my problem with sound:
[http://ubuntuforums.org/showthread.php?t=938497&highlight=compaq+CQ45]("http://ubuntuforums.org/showthread.php?t=938497&highlight=compaq+CQ45")

---

### Post by hmarkg on 2008-10-17
Thank you once again

---

### Post by hmarkg on 2008-11-02
Ubuntu 8.10 is very good. A lot of bug is solved haha... Power management is also improved... Wifi works like oil, smooth smooth... But sound still got problem...

---

