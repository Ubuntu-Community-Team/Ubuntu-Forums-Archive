---
title: "mounting windows partion in persistent usb install of 9.04"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by wolfganggold on 2009-09-15
Hello folks,
I've been trolling various forums for an answer to this and can't figure it out.  I have a persistent install of 9.04 on a 4GB USB stick.  It updates and saves my changes beautifully.  The first time I booted with it, I was able to see the existing NTFS partition on the system's internal drive but on subsequent boots I get an error that the drive can't be mounted.  The error is "mount:according to mtab, /dev/sda2 is already mounted on /media/disk"

When I look in /media, there's nothing there.  There are two hidden files, .hal-mtab and .hal-mtab-lock ...I've deleted .hal-mtab to no avail.

I want to use this drive to boot to unresponsive Windows systems and scan them for viruses from Ubuntu but this problem is keeping me from doing so.  Any ideas?

##################################################

OK, I've solved my own problem!  I said above that I deleted .hal-mtab to no avail.  I hadn't however rebooted after that.  Upon reboot, I WAS able to successfully mount the Windows volume.  The key here is to remember to UNMOUNT that volume when you shut down.  When you do that, you can mount windows volumes on other systems with ease!  I thought I'd go ahead an post this just in case someone else was having a similar problem...Hope it helps!

---

### Post by swerdna on 2009-09-15
> **wolfganggold said:**
> 

OK, I've solved my own problem!  I said above that I deleted .hal-mtab to no avail.  I hadn't however rebooted after that.  Upon reboot, I WAS able to successfully mount the Windows volume.  The key here is to remember to UNMOUNT that volume when you shut down.  When you do that, you can mount windows volumes on other systems with ease!  I thought I'd go ahead an post this just in case someone else was having a similar problem...Hope it helps!
As far as the usb stick is concerned, the ntfs drive is always there whenever you boot Ubuntu. So you cabn mount it permanently in the fstab of Ubuntu. You don't have to mount it each time you boot and unmount it before you shut down. If you have it mounted in fstab it will be unmounted cleanly on shutdown.

Ref: [HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubuntfs.html")

PS: just noticed -- it's a travelling USB stick so this might not suit you.

---

### Post by wolfganggold on 2009-09-16
Yep...being able to do this is hella cool!  I think this may be the best way to scan a windows drive for viruses.  Even safe mode loads crap you don't want.  I can go anywhere and lay the smack down!  :)

---

