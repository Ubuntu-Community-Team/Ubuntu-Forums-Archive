---
title: "USB LCD Display"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by nogi on 2011-08-24
I bought a [generic USB LCD display ]("http://www.ebay.com.au/itm/320689136780?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649")off eBay which apparently should work under Linux. I haven't used Linux since Slackware v2 so consider me very very green on the OS. I've tried searching this forum on how to get this display to work but am getting more and more confused.
 
Is there a dummy's guide to getting a LCD (connected via USB) to work under 11.04 (64-bit)? I've installed LCDProc of the software manager and tried to configure it but no change on the display.

---

### Post by LowSky on 2011-08-25
here is the official documentation for LCDproc
[http://lcdproc.sourceforge.net/docs/current-user.html](http://lcdproc.sourceforge.net/docs/current-user.html)

here is someone blog on getting it to run
[http://linuxserver2011.wordpress.com/2011/03/25/getting-the-lcd-to-work-with-lcdproc/](http://linuxserver2011.wordpress.com/2011/03/25/getting-the-lcd-to-work-with-lcdproc/)

looks like a great learning project.

EDIT: The also have their own forums
[http://forums.lcdsmartie.org/](http://forums.lcdsmartie.org/)

---

### Post by nogi on 2011-08-25
Ok, I've followed and installed but no go on the display. I think it's because I haven't got the correct port setup. How do I know what /dev/ device to use? 

Using dmesg I get:
[SIZE=1][FONT=courier new][ 8361.435220] usb 4-3: USB disconnect, address 2[/FONT]
[FONT=courier new][ 8365.450219] usb 4-3: new low speed USB device using ohci_hcd and address 3[/FONT]
[/SIZE]
and with lsusb i get:
[SIZE=1][FONT=courier new]root@KAL-EL:/home/nogi# lsusb[/FONT]
[FONT=courier new]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
 [FONT=courier new]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=courier new]Bus 004 Device 003: ID 0403:c630 Future Technology Devices International, Ltd lcd2usb interface[/FONT]
 [FONT=courier new]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=courier new]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
 [FONT=courier new]Bus 002 Device 002: ID 0624:0248 Avocent Corp. [/FONT]
[FONT=courier new]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
 [FONT=courier new]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

A ls -ltr /dev/ to get the last updated device
[http://pastebin.com/edzZJjHg](http://pastebin.com/edzZJjHg)

My LCDd.conf:
[http://pastebin.com/vgh6vdnU](http://pastebin.com/vgh6vdnU)

[/FONT][/SIZE]

---

