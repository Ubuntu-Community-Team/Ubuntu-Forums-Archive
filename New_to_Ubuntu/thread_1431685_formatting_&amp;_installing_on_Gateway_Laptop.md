---
title: "formatting &amp; installing on Gateway Laptop?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by garyed on 2010-03-16
I have a 5 year old Gateway laptop with XP that won't boot.
It has a restore partition & it locks up after restoring the whole system so I decided to try Jaunty live CD & everything works fine except fot the wireless card. I want to completely reformat the drive & install Jaunty but
I want to make sure the HD is tested & mark any bad sectors. Can I do this with the live CD or do I need something else. I also want to clean out the recovery partition too. I was also wondering why the recovery partition(fat32) is sda2 yet its starting block is at "1" in fdisk. The Windows partition(NTFS) is   
sda1 but it starts on a higher number block. Where would the MBR be?

---

### Post by lkraemer on 2010-03-16
Why don't you try the information here first?
[http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)
You might get XP booting properly by following these steps.

If that doesn't work, I'd backup all the files and Data you need to
save, then proceed.  You may want to just purchase a new 250 or 500 Gig
drive and Install Ubuntu on it.  

If you want to use the existing drive, I'd check it to determine the 
Manufacture and download their diagnostics.  Run the Diagnostics to
determine the state of the drive.  Most drive Diagnostics write over
your data, so make sure it's saved or moved somewhere safe.

For the Gateway Wifi try these commands from the LiveCD.
Just use "copy & paste" for each command.
And, there is a difference in LSPCI and lspci.
```

uname -r
lspci
lspci -nn
lsusb
lshw -C network
lsmod
cat /etc/modprobe.d/blacklist.conf
iwconfig
ifconfig

```
Just copy & paste the commands in a Terminal window,
one at a time, and post the results.
(If you are using versions earlier than 9.04 use:
cat /etc/modprobe.d/blacklist)
From this information we will know more about the Wifi.

lk

---

### Post by garyed on 2010-03-16
I'm not that worried about the wifi yet.
lspci picks up the wifi its a BCM4306 Broadcom Gemtek.
I searched for the linux drivers but I don't think they have any. 
I'm more concerned about the HD, I'm thinking it could have bad sectors causing it to lock up & not boot.
There's nothing I need to keep on the HD so I just want to clean it off & start from scratch. I just don't know about the recovery partition either.

---

### Post by lkraemer on 2010-03-17
You're booting problem is most likely a Windows virus causing the
problem.  A fresh install of the M$ Software on a clean partiton
will most likely fix your problem.  You should have made a set of
Recovery CDR's or DVD's when you first booted the Gateway.  Those
can be used to fix your problem.  The RECOVERY Partition was typically
immediately after the XP Partition unless that has changed.
 
You haven't said what Version of Ubuntu you are using for the
LiveCD, or what Version you are wanting to install.  Plus folks
need to know if it's 32 bit versus 64 bit when they assist you.
Ubuntu does support the Broadcom Wifi cards, and you have a couple
of choices to make the Wifi functional.

Is your Hard drive IDE or SATA?

I don't understand what you want to know about the RECOVERY Partition.
It's never used, unless you try to restore the OS.  It just sits there
taking up about 10 Gig (if I remember correctly).  Since you aren't
wanting to save it, you can just delete it, but if I were in your shoes,
I'd just purchase a new Hard Drive, install it and be on my way,
keeping the old one for future use after you're up and running.
That gives you the possibility to access old documents and/or files
that you may need later by using a USB Adapter on the old drive.

The price of a new hard drive is going to be less than software to diagnose
the possible defective hard drive.  Spinrite is a good Diagnostic tool that
gives good results.  You can always download the Manufactures Software to
test the drive.  SOME tests are DESTRUCTIVE for you're data.

What M$ Software is a MUST HAVE when you are running Ubuntu?
ie, Quicken, M$ Paint, etc.
 
One other quick point...... When someone gives you a list of Terminal
Commands, it's information they need to assist you since they can't see
your display, or type on your keyboard.  It might be good for future
postings to give a bit more detail.......Enough said!

lk

---

