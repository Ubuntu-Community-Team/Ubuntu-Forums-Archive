---
title: "wireless not recognize in eee 1005"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by snail100 on 2010-03-29
hi, need help
i got eee pc 1005. the wirelss network works fine with  windows 7 starter and format the computer.
1. i installed ubuntu 9.10  netbook remix. 
2.the lan connection works fine.
3.the wireless  connection doesn't work- no icon on the tray, no detection of any  network- nothing. help please!
im newbie so help in laymen terms. 
thanks

---

### Post by mikeyphi on 2010-03-29
Welcome!

I've not had any problems on my 701 eeepc however, I guess you could have a different wireless setup. Have a look at this site - it's not specifically for the 1005 but may help:
[http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt](http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt)

---

### Post by undecim on 2010-03-29
> **snail100 said:**
> hi, need help
i got eee pc 1005. the wirelss network works fine with  windows 7 starter and format the computer.
1. i installed ubuntu 9.10  netbook remix. 
2.the lan connection works fine.
3.the wireless  connection doesn't work- no icon on the tray, no detection of any  network- nothing. help please!
im newbie so help in laymen terms. 
thanks

Usually, the easiest way to get proprietary wireless drivers working is as follows:

1: Connect to the internet via an ethernet connection
2: Open the "Update Manager" from System -> Administration -> Update Manager but don't update anything (this updates your package listings, so that your driver will show up in the next step)
3: Open "Hardware drivers" from System -> Administration -> Hardware Drivers. Install your wireless driver here.

If your wireless driver isn't listed, then open a terminal, and copy and paste this text into it:
```
lspci
```
press enter and post the output here

---

### Post by snail100 on 2010-03-29
hi, thanks for the quick reply .... i will try it.... thanks:D

---

### Post by snail100 on 2010-03-29
hi undecim,
here my result from lspci:

00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)

from "sysinfo" the card is:
 
Atheros communication inc. device 002c (rev 01)
subsystem:device 1a3b:1112

thanks

---

### Post by bkratz on 2010-03-29
This thread seems to be about your device and has several "wow I got it to work" comments.

[http://joeb454.ubuntuforums.org/showthread.php?p=8700392](http://joeb454.ubuntuforums.org/showthread.php?p=8700392)

Hope it helps

---

### Post by snail100 on 2010-03-29
hi, 
 thanks for the comment i am using now NDISWRAPPER and it works (i know i am green....:)) but i would like to use ubuntu native like madwifi, i think, any way thanks

---

