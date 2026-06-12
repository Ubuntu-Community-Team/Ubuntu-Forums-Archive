---
title: "Total disaster trying to set up Verizon EVDO device"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by theosib on 2008-09-07
I'm having a heck of a time trying to figure out how to get this Verizon EVDO device working with my Ubuntu box, and I was hoping someone here might help.

I've read a bunch of things online, such as these:

[http://www.markmmanning.com/blog/2007/07/installing-verizon-wireless-evdo-card.html](http://www.markmmanning.com/blog/2007/07/installing-verizon-wireless-evdo-card.html)
[http://kenkinder.com/evdo-pc5740/](http://kenkinder.com/evdo-pc5740/)

This is a USB wireless modem.  When I type 'lsusb', it comes up like this:

Bus 003 Device 002: ID 106c:3711 Curitel Communications, Inc. 

The docs talk about a device ID 0x3701, which must be at least slightly different, but I can't even get far enough to find out.

The first problem I run into is that the device doesn't show up in /proc/bus/usb like the instructions say.  As I say, it appears when I type lsusb, but in fact, there is _nothing_ in /proc/bus/usb.  This is what I get in /var/log/messages:

Sep  7 14:18:43 josh-desktop kernel: [ 1510.658204] usb 3-3: new high speed USB device using ehci_hcd and address 2
Sep  7 14:18:43 josh-desktop kernel: [ 1510.797992] usb 3-3: configuration #1 chosen from 1 choice
Sep  7 14:18:43 josh-desktop kernel: [ 1510.798863] cdc_acm 3-3:1.0: ttyACM0: USB ACM device
Sep  7 14:18:43 josh-desktop kernel: [ 1510.821251] scsi3 : SCSI emulation for USB Mass Storage devices
Sep  7 14:18:48 josh-desktop kernel: [ 1515.820577] scsi 3:0:0:0: Direct-Access     PANTECH  Mass Storage     0001 PQ: 0 ANSI: 0 CCS
Sep  7 14:18:48 josh-desktop kernel: [ 1515.834500] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Sep  7 14:18:48 josh-desktop kernel: [ 1515.834551] sd 3:0:0:0: Attached scsi generic sg3 type 0

So, it sees the device and correctly gives is a node at /dev/ttyACM0, but then it seems to see it as a mass storage device, which may be the start of the problems.

I've set up pppd according to the instructions with the two script files, but I don't get anything informative to help me to debug it.  The only messages I see in /var/log/messages when I start up pppd are:

Sep  7 14:29:21 josh-desktop pppd[10258]: pppd 2.4.4 started by root, uid 0
Sep  7 14:29:23 josh-desktop pppd[10258]: Exit.

Can anyone help me out with some next steps here?  Networking is my weak point, and dealing with this USB device is going to be black magic.  If Ubuntu is trying to be 'smart' and treats it as a mass storage device, I have no hope of figuring out how to make it not do that without some help.

Thanks!!!

---

### Post by theosib on 2008-09-08
I'm going to try bumping this once before I try posting somewhere else.  Can anyone make a suggestion?

---

### Post by timcredible on 2008-09-08
it'll work fine, click on my sig, i have a how-to article on my website about this.

---

### Post by ziesemer on 2008-09-26
(timcredible - Sorry, but it appears your article makes assumptions not applicable here, particularly the device.)

I seem to be having the exact same issue as theosib, and all the same troubleshooting steps.  I've also read just about every page I could find regarding support for EVDO devices under Linux, including all 28+ pages of [http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989) .

The USB product ID is slightly different than theosib's, but I'm having the exact same symptoms.  For me, lsusb shows 0x3b03 for the idProduct (still with 0x106c for the idVendor).  This is a Pantech UM175AL - which is Alltel / CDMA, same as Verizon.  (I'm wondering if the "AL" is a revision specific to Alltel?)

Under Windows, I can see the 0x3b03, which is the "flash drive" / USB Mass Storage component that contains the Windows/Mac drivers.  But I also see the USB Serial component, which is 0x3715.  Unfortunately, I can't find this 0x3715 part of the "composite device" anywhere under Linux.  It's as if it finds the mass storage portion, then quits looking for more.

I followed the instruction at [http://ubuntuforums.org/showpost.php?p=4205671&postcount=153](http://ubuntuforums.org/showpost.php?p=4205671&postcount=153) , involving modprobe and usbserial, but to no avail.

Unlike theosib, I don't even have any mention of cdc_acm, ttyACM, or "USB ACM" anywhere in my logs.  I also don't get any /dev/ttyACM* or /dev/ttyUSB* devices created.

I'm running a clean install of Ubuntu Hardy Heron with all the latest updates as of today (2008-09-26), kernel 2.6.24-19.

It certainly seems that any troubleshooting of pppd, etc., is first dependent on finding a device that it can work with.

Any help would be greatly appreciated.  Thanks!!

---

### Post by theosib on 2008-09-27
Somewhere else, someone pointed to this:

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Apparently, some of these devices appear as USB mass storage so that the driver can be loaded from it (for Windows).  Using this mode switch program may fix that problem.  I haven't had a chance to test it yet.  Right now, we're using a Mac sharing its internet connection, and that's stable.

---

### Post by ziesemer on 2008-09-27
> **theosib said:**
> Somewhere else, someone pointed to this:

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Apparently, some of these devices appear as USB mass storage so that the driver can be loaded from it (for Windows).  Using this mode switch program may fix that problem.  I haven't had a chance to test it yet.  Right now, we're using a Mac sharing its internet connection, and that's stable.

Thanks.  I was able to download, compile, and run it.  Unfortunately, the simple "disconnect" option isn't enough.  Apparently I also need a message and endpoint to send, and I've not yet seen any details on how to obtain them.

Thanks!

---

### Post by ziesemer on 2008-09-27
Finally - success!!  I found the needed message by sniffing the USB traffic under Windows.

I've documented this all on my blog at [http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html](http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html).

---

