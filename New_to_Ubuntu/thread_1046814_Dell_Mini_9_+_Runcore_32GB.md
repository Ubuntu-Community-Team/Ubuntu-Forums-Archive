---
title: "Dell Mini 9 + Runcore 32GB"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by BeyondSpectrality on 2009-01-21
So I've been working with Ubuntu for a little over a week now and have made a few adjustments here and there and am fairly familiar with an assortment of sudo commands and what not but I recently cloned my ubuntu install to a new hard drive.

My problem is in the fact that I have almost 30GB of unallocated space and I have gparted but it wont let me adjust the partition because it is mounted and I can't unmount it due to the fact that I don't have an external CD/DVD drive or a bootable USB so running gparted live isn't possible. Can anyone help me with a way to expand the partition so I can make use of that extra space without access to these other things?

Thank you in advance,
Phil

P.S. Yes I did a search and read similar threads....nothing helped....at least not that I found.......

---

### Post by yeats on 2009-01-21
So did you install with a USB drive?  You'll have to run a Live CD/USB to repartition your hard drive - it can't be mounted when you do it. . . .

---

### Post by BeyondSpectrality on 2009-01-21
Looks like I'll have to wait until I can afford anb external DVD drive....

And no my system came pre-installed with Ubuntu....

---

### Post by handydan918 on 2009-01-21
> **BeyondSpectrality said:**
> Looks like I'll have to wait until I can afford anb external DVD drive....

And no my system came pre-installed with Ubuntu....

No, no, no. You can install 8.10 on a USB stick, and run it as a live cd from there. 
Alternatively, you could format the unallocated space as ext3 and simply modify /etc/fstab to utilize the new partition as you see fit.

---

### Post by BeyondSpectrality on 2009-01-23
Okay new problem...i can't make a usb bootable unless i can run the ubuntu 8.10 ISO.

Well I'm on a 32GB SSD that is partitioned for my previous 4GB SSD leaving me with less than 150MiB....

So I have the ISO file on an SD card but the Terminal mount command doesn't seem to find it and AcetoneISO2 just finds things in the main directories...so my problem is that I can't find a way to mount the ISO to allow the making of the live USB....

Edit: Thanks for the help everyone I figured it out, I ended up using Portable Linux. It happened to read the ISO file that was on my SD card and loaded it onto my USB!

---

