---
title: "Newbie--Need Help Connecting"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by pennstaterav4 on 2007-04-22
I am really new to ubuntu, and i have the 6.10 version, and i just cant seem for the life of me how to connect to the wireless network. I am in the network manager, and i have tried all of that stuff, and i just cant seem to get it. Is there anyone out there that will sit with me and help me figure this out, because I have a wireless linksys card in my desktop, and i have tried my usb microsoft wireless card, and i am getting no results. Is there a way to just search for the wireless networks in range and click connect like windows?

Thanks

--Ricky

---

### Post by Floppyjoe on 2007-04-22
Getting Wireless to work in Linux is usually a bit more complicated than in windows.
If you can open a terminal and execute a couple of commands you could get started on your way.
To open a terminal click on Applications/Accessories/Terminal.
Enter the following for a USB device:
```
lsusb
```
and for A PCI device enter the following:
```
lspci
```

Post the output here.

---

### Post by pennstaterav4 on 2007-04-22
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub inte
rface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Cont
roller (rev 02)
00:1e.o PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Brid
ge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller
(rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 0
2)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) A
C'97 Audio Controller (rev 02)
01:00.0 VGA compatible driver: nVidia Corporation NV34  [GeForce FX 5200]  (re
v al)
02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:02.0 Network Controller Broadcom Corporation BCM4306 802.11b/g Wireless LAN
Controller (rev 03)
02:08.0 Ethernet Controller: Intel Corporation 82562EZ 10/100 Ethernet Controlle
r (rev 02)

I think that is what you wanted...it took me a long time to type it :-P lol

---

### Post by Floppyjoe on 2007-04-22
> Network Controller Broadcom Corporation BCM4306 802.11b/g Wireless LAN
Controller (rev 03)
That is your wireless card there.
(1)You can either use the bcm43xx driver with the firmware.
or
(2)You can use ndiswrapper and the windows drivers that you aquire from your computer manufacturers website.

This link is for edgy but probably will still work.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

---

