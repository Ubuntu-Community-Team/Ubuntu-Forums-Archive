---
title: "Dell TrueMobile 1400 /b/g"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by Lindsay Cole on 2007-02-25
Hello,

I have made the switch completely to Ubuntu 6.1. Big change- everything went flawlessly- I even have World of WarCraft up and running- and media works fine.

The only flaw, is the internal Dell wireless card that came with me Dell Inspiron XPS (Generation 1- 3.40 GHz, 1GB PC3200 RAM, Radeon 9700 Mobility)- it is a Dell TrueMobile 1400- does anyone have any instructions on how to get this working? Keep in mind, I am still a little inexperienced with Linux (so when people say use ndiswrapper- I have no idea what they are talking about).

If anyone can help, that would be great- can't wait to get wireless up and running on this again.

Thanks in advance!

---

### Post by Lindsay Cole on 2007-02-25
Anyone at all?

---

### Post by gradedcheese on 2007-02-25
You'll need to tell us the chipset.  Open a terminal via Applications->Accessories->Terminal and type in "lspci" and press Enter.  There will be a bunch of output, post the line(s) starting with "Ethernet Controller" (or the entire thing) here.

---

### Post by Lindsay Cole on 2007-02-26
lindsay@xps:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
**_02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)_**
lindsay@xps:~$ 

And now the fun begins :)

---

### Post by gradedcheese on 2007-02-27
Not much fun: Broadcom is highly unsupported.  You will get it to work via ndiswrapper, search for that and "4306" in the forums to find a howto post about it (it's definitely there).

---

### Post by Lindsay Cole on 2007-02-27
[http://www.ubuntuforums.org/showthread.php?t=340689&highlight=ndiswrapper+4306](http://www.ubuntuforums.org/showthread.php?t=340689&highlight=ndiswrapper+4306)

Perfect!

Thanks!

---

