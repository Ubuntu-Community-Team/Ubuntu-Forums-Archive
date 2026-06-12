---
title: "suspend problem help"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by blake7 on 2009-11-11
suspend problem help
hi when i try to suspend or hibernate it fails to go though with to whole proses.
what happens is that it close down all operations and then makes the sceen go blank (but you can still see its charge)
then my lcd moon logo starts blinks confirming suspend but that it, it stops at that point with the sceen blank but still with the current going though and i cant do anything with my laptop and all functions are dead on my laptop ibm x60s and my only opption at this point is to pull the plug and reboot

please can u helpp
thank you

---

### Post by jbrown96 on 2009-11-11
I replied to your post yesterday. We need more information from you. Please post the output of those commands.

---

### Post by blake7 on 2009-11-11
cheers i do that 


not sure how all this fourm thing workss so i repeated massage

---

### Post by blake7 on 2009-11-11
dude@dude:~$ lspci


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)

---

### Post by blake7 on 2009-11-11
dude@dude:~$ tail -f 20 /var/log/Xorg.0.log
tail: cannot open `20' for reading: No such file or directory
==> /var/log/Xorg.0.log <==
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "0x0"x0.0    0.00  0 0 0 0  0 0 0 0 (0.0 kHz)
(II) PM Event received: Capability Changed
I830PMEvent: Capability change

---

### Post by blake7 on 2009-11-11
dude@dude:~$ tail -f 20 /var/log/kern.log
tail: cannot open `20' for reading: No such file or directory
==> /var/log/kern.log <==
Nov 11 20:10:03 dude kernel: [   43.238175] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 11 20:10:14 dude kernel: [   53.920093] wlan0: no IPv6 routers present
Nov 11 20:11:03 dude kernel: [  103.445627] wlan0: disassociating by local choice (reason=3)
Nov 11 20:11:16 dude kernel: [  116.264902] wlan0: authenticate with AP 00:1f:9f:88:60:a5
Nov 11 20:11:16 dude kernel: [  116.267120] wlan0: authenticated
Nov 11 20:11:16 dude kernel: [  116.267128] wlan0: associate with AP 00:1f:9f:88:60:a5
Nov 11 20:11:16 dude kernel: [  116.269982] wlan0: RX AssocResp from 00:1f:9f:88:60:a5 (capab=0x411 status=0 aid=2)
Nov 11 20:11:16 dude kernel: [  116.269989] wlan0: associated
Nov 11 20:12:42 dude kernel: [  202.593734] CE: hpet increasing min_delta_ns to 15000 nsec
Nov 11 20:12:58 dude kernel: [  218.055772] CE: hpet increasing min_delta_ns to 22500 nsec

---

### Post by blake7 on 2009-11-11
i hope that mean somthing to you

thank you for your time and if you have any more request then please feel free to ask

---

### Post by jbrown96 on 2009-11-11
I've had some trouble suspending my T61p with 9.10 as well. Your hardware is very similar to mine. Try disabling your wireless card before you suspend. My Thinkpad has a hardware switch, but I think the X60s lack this. Right click on the network icon and uncheck "enable wireless."

I found the suspend log. Post output from ```
cat /var/log/pm-suspend.log
```

---

### Post by blake7 on 2009-11-11
i ttry that but is thier nothing a that csan just sort out the problem????

---

### Post by blake7 on 2009-11-11
ps it does have a hard switch

---

### Post by blake7 on 2009-11-12
hi can any help 
ive tryed all suggestions and it still does not work 

it was fine in 9.04 can the program from that be inported in to 9.10

hope you can help 

thank you

ps i love 9.10

---

