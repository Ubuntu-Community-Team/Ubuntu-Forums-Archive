---
title: "SD card reader driver"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-09-09
I need a driver for my SD card reader for linux. It's actually a multi card reader. Not sure if it matters what computer I have or not, but it's a alienware sentia 223.

---

### Post by RedSingularity on 2009-09-09
My laptop has an SD card reader built in as well.  Whats the problem exactly?

---

### Post by kakashi_12 on 2009-09-09
I put in the card and nothing happens. It won't show up in my computer or "places", no autoplay.

---

### Post by RedSingularity on 2009-09-09
Put it in, wait a minute, and post the output of

sudo fdisk -l

---

### Post by Darkwing-Duck on 2009-09-09
I know on my ACER netbook it has a problem with reading it. The workaround I found is to boot it with the SD card in it and it will read it. Maybe try this and see if it is part of that bug?

---

### Post by kakashi_12 on 2009-09-15
Neither of those worked. The command just gave me info on my partitions, didn't help at all.

---

### Post by kakashi_12 on 2009-09-16
bump (aka, please help)

---

### Post by kakashi_12 on 2009-09-17
bump

---

### Post by jamieleshaw on 2009-12-17
Actually just a moment
just post lspci output

---

### Post by kakashi_12 on 2009-12-17
huh

---

### Post by scratman on 2009-12-18
Simply type ```
lspci
``` into terminal and post the result.  It may be the case that this is a long output, and if this is causing problems, type 
```
cd
lspci >> lspci.txt
```
into Terminal, then go to your home directory, open the file called lspci txt and post the contents.

---

### Post by kakashi_12 on 2009-12-19
no, sorry. did not help.

---

### Post by daemonkity on 2009-12-19
> **kakashi_12 said:**
> no, sorry. did not help.

No, Kakashi, I meant did it help the person who asked for the lspci to be posted in the first place, hence the quote.

---

### Post by kakashi_12 on 2009-12-19
oh, oops. sorry, my mistake.

---

### Post by Sef on 2010-01-24
Applications > Accessories > Terminal

Then copy and paste this code:

 	Code:
 	lsusb 
Then copy and paste the results here.

That code will list your usb devices - both internal and external.

---

### Post by kakashi_12 on 2010-01-26
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by kakashi_12 on 2010-02-03
bump

---

### Post by ironside on 2010-02-05
Ok I have the same problem with my internal SD reader not working. I know the SD reader hardware works fine as it worked when my ASUS s101h had window. But its never worked since I install ubuntu. I have tried rebooting with the sd card in. No luck. Here is a readout;

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

---

### Post by kakashi_12 on 2010-02-23
ok, still nothin' here.

---

