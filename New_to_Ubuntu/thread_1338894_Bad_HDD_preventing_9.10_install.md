---
title: "Bad HDD preventing 9.10 install?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by specialedster14 on 2009-11-26
I was running 9.04 on my eee pc 900ha and I decided I wanted to do a clean install of 9.10.  I knew that my hdd was possibly starting to go bad (with a few bad sectors), but I now know it is getting far worse.  I downloaded 9.10 and made a usb install disk.  The first time I installed it seemed to install okay, until the desktop appeared when an error message appeared saying a couple of processes had failed and my desktop appeared frozen.  After I restarted I couldn't log in with my previously assigned user name and password.

I decided to try a clean install again, which again seemed to work, except that the same errors appeared on the desktop and the disk utility reported that my hdd has "many bad sectors" (nearly 900).  After restarting again I had the same login problems as before.

I tried a clean install for the third time and this time didn't even get to the desktop.  At about 30% the installation fails with errno 30:

[Errno 30] Read-only file system

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

It now does this every time I try to install.  I even tried making another usb install disk with a different download, but had the same result.  I am thinking the problem is my hdd, but I'd like to know for sure before I go out with the masses tomorrow to buy a new one.  Anybody have knowledge of this?

---

### Post by Rx.WDZ on 2009-11-27
I Don't think its the harddrive I had a similar problem on a Celeron System try enabling "NOAPIC" in the boot parameters. With that many bad sectors though, I'd personally buy a New Harddrive.

---

### Post by efflandt on 2009-11-27
Normally a drive reserves extra sectors to automatically swap with any bad sectors.  But if bad sectors actually start visibly showing up, that is a bad sign that the drive is failing, and it is best not to use it for anything essential.

I tried to use a 60 GB drive on an older PC (PIII 550 w/320 MB RAM).  When I used gparted-live CD to create 27 GB ext3 sda1, swap sda2, and 27 GB ext3 sda3, gparted could not even identify the filesystem type of the sda3 it had just created/formatted.  I tried making a 40 GB hda1 and that failed, but I was able to create a 32 GB sda1 and swap sda2 that seemed to work with the rest unallocated.

I later was somehow able to create/format sda3 on a P4 2 GHz PC, but when I did e2fsck -cckfv /dev/sda3 to lock out badblocks, I gave up after 12 hours @ less than 45% completed.  And when I installed Linux on just sda1, SMART during boot reported "Drive failure is Imminent" due to all the badblocks marked by e2fsck.  So I will not use that drive.

---

