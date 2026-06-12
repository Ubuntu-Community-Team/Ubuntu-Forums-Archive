---
title: "Exclamation  [HELP] Smart Link SmartUSB56"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by nookadum on 2005-07-25
**EDIT:** Whoops, I accidentally posted this same message the first time in the Warty 4.10 Networking section.  :-# Sorry! Can a mod please delete that post? It's located [here](http://ubuntuforums.org/showthread.php?t=51537).

Hi guys, I'm a Debian/Ubuntu (package) newbie here, but I have worked with FreeBSD and Linux (Slackware 8.1+ specifically) so I know how to install applications through basic CLI commands. :)

Despite my knowledge, I have no idea how to install (and get it to work) my USB modem. The modem is a **SpeedCom+ v.90/56k USB modem**, which is basically your dreaded **SmartUSB56** (*Smart Link USB*) modem. I followed all the guides pertaining to the Smart Link line of modems, like:

[http://www.raspberry.co.za/michael/?page_id=2](http://www.raspberry.co.za/michael/?page_id=2)
[http://ubuntuforums.org/showthread.php?t=21940&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=21940&page=1&pp=10)
[http://linmodems.technion.ac.il/archive-fourth/maillist.html#00176](http://linmodems.technion.ac.il/archive-fourth/maillist.html#00176)
[http://www.linuxquestions.org/questions/showthread.php?postid=1752276](http://www.linuxquestions.org/questions/showthread.php?postid=1752276)
[http://www.linuxquestions.org/questions/showthread.php?postid=1684439](http://www.linuxquestions.org/questions/showthread.php?postid=1684439)

I installed the proper packges, gotten directly from here. The files are:

[B]sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb
sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb[/B]

Of course I installed **sl-modem-modules** first, or else installing daemon would give a dependancy error.

Anyways, the installation of both those packages were successful. I think. It ended with:

[FONT=Lucida Console]symbolic link `/dev/modem' -> `/dev/ttyS0' created.[/FONT]

But the _/dev/modem_ link is BROKEN. However _/dev/slamr0_ to _/dev/slamr3_ and _/dev/slusb0_ to _/dev/slam3_ are installed, but I cannot access them, nor make a proper link to them.

If I **slmodemd** any of the slamr and slusb devices, it gives me this error:

[FONT=Lucida Console]error: mdm setup: cannot open dev `/dev/slusb0': No such device or address
error: cannot setup device `/dev/slusb0'[/FONT]

What the hell? Now my device is connected to my PC, and it identifies in **lsusb** like so:

[FONT=Lucida Console]Bus 005 Device 009: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem[/FONT]

But I still can't get it to work. However, I did try to look in my **lsmod** list to see if it loaded slamr or slmod properly, and guess what. It didn't. The _slamr.ko_ and _slusb.ko_ drivers are stuck in my /lib/modules/2.6.10-5-386/misc, and I did try to load them manually with:

[FONT=Lucida Console]sudo insmod slamr.ko
sudo insmod slusb.ko[/FONT]

_slamr.ko_ loads okay (but it's useless since my device is USB) but slusb.ko gives me this error:

[FONT=Lucida Console]insmod: error inserting 'slusb.ko': -1 Unknown symbol in module[/FONT]

_**So.. what I'm asking for is help in getting my modem to work, or at least getting slusb.ko to load so Ubuntu can detect my modem and load the driver properly.**_ Otherwise it just gets detected like this:

[FONT=Lucida Console]Jul 24 23:23:22 localhost kernel: usb 5-3.1: new full speed USB device using ehci_hcd and address 10[/FONT]

When it should be similar to or like this:

[FONT=Lucida Console]usb.c: deregistering driver ST7554 USB Modem
 hub.c: new USB device 00:07.2-1, assigned address 2
 usb.c: USB device 2 (vend/prod 0x483/0x7554) is not claimed by any 
active driver.
 ST7554 USB Modem.
 usb.c: registered new driver ST7554 USB Modem
 <6>slusb: slusb0 is found.
 usb.c: registered new driver acm[/FONT]

So please try and help me. :)  ](*,)

---

