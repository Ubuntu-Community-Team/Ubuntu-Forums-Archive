---
title: "can't get rid of Fedora"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by wjm on 2010-03-22
Well, this is embarrassing but I'm slowly transitioning servers at work from Fedora to Ubuntu-Server.  Everything is going really smooth until I decide to nuke my Fedora installation at home.  I've formatted the USB drive in Fedora, set the partition properly, made it bootable and then used unetbootin to copy the 64-bit alternate ISO onto my USB key.  When I reboot the machine, boot from USB the normal SYSLINUX prompt comes up for about a quarter of a second then the screen goes blank.

I've tried:

Using FAT16/FAT32
Changing the DISKLABEL to something less than five characters
formatting it over/over again and re-trying
Downloaded the ISO from four different FTPs and tried bittorrent twice

I'm completely lost - this has NEVER happened before and I'm almost at the point where I throw my tower out the window screaming "sic sempre tyranus! Redhat!"

EDIT:

I am going to try to grab the Live Desktop Image and then check the MD5 on it and see if that won't work either.

---

### Post by johngreth on 2010-03-22
I've had this problem before. I fixed it on Ubuntu by formatting the usb drive with "USB Startup Disk Creator" before installing the OS with UnetBootin. I don't know what the "USB Startup Disk Creator" does differently than other format tools, but that may be the problem.

---

### Post by bodhi.zazen on 2010-03-22
> **wjm said:**
> Well, this is embarrassing but I'm slowly transitioning servers at work from Fedora to Ubuntu-Server.  Everything is going really smooth until I decide to nuke my Fedora installation at home.  I've formatted the USB drive in Fedora, set the partition properly, made it bootable and then used unetbootin to copy the 64-bit alternate ISO onto my USB key.  When I reboot the machine, boot from USB the normal SYSLINUX prompt comes up for about a quarter of a second then the screen goes blank.

I've tried:

Using FAT16/FAT32
Changing the DISKLABEL to something less than five characters
formatting it over/over again and re-trying
Downloaded the ISO from four different FTPs and tried bittorrent twice

I'm completely lost - this has NEVER happened before and I'm almost at the point where I throw my tower out the window screaming "sic sempre tyranus! Redhat!"

EDIT:

I am going to try to grab the Live Desktop Image and then check the MD5 on it and see if that won't work either.

The alternate CD does not work with unetbootin, you have to use the Desktop CD. Not sure about the server CD but I suspect it will not work either.

---

