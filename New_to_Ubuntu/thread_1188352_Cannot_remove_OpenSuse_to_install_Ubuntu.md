---
title: "Cannot remove OpenSuse to install Ubuntu"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Hardhat_Harry on 2009-06-15
Hi,

I have started down the Linux path and started with OpenSuse 11.1 but after struggling to install applications I want to remove OpenSuse now install Ubuntu 9.04.

The trouble is when I install Ubuntu it says there is no Operating Systems installed on the computer and reports the partition which OpenSuse resides (sba) as 40Gb, not 80Gb as it should be. I have tried deleting sba and installing Ubuntu into the new partition but the PC just boots into OpenSuse

I have tried booting up using the Gparted live CD latest stable version to try and resolve this and delete and remake the partition but it has still booting after 24 hours with the message 1955.176001 [<c1013462>]?syscall_call+0x7/0xb

The PC is i586.

Thanks for any help.

---

### Post by Therion on 2009-06-15
If you know your PC will boot from a CD but your gParted LiveCD is giving you problems, I would try burning a new gParted LiveCD.  

Did you burn the CD SLOWLY, as in 8x or close to it?  You need accuracy for this project, not speed.  

If that continues to fail I'd suggest you try using **Boot and Nuke** to wipe the drive and start with a fresh install:

[http://www.dban.org/download](http://www.dban.org/download)

---

### Post by pastalavista on 2009-06-15
Boot from the Ubuntu Live CD and select "Try without changing..." does this work? Can you load the desktop? Go to System > Administration and select partition editor. Right-click the drives and select 'unmount' and then delete the entire drive (except for partitions for dual boot, data, etc)

And then run the installer program from the desktop.

---

### Post by redbook4574 on 2009-06-15
> **pastalavista said:**
> Boot from the Ubuntu Live CD and select "Try without changing..." does this work? Can you load the desktop? Go to System > Administration and select partition editor. Right-click the drives and select 'unmount' and then delete the entire drive (except for partitions for dual boot, data, etc)

And then run the installer program from the desktop.

Beat me to it, that's exactly wot I had to do!!!!

---

### Post by Hardhat_Harry on 2009-06-15
Ok I'm booting from the Ubuntu CD now will let you know what happens. Thanks for the Quick Response!!!!

---

### Post by ugm6hr on 2009-06-15
The default "Guided" installation for Ubuntu 9.04 is now to try and dual-boot rather than wiping your HD (as previous versions did).

So I suspect that when it reports it as 40GB, it is actually suggesting that it will shrink the Suse to 40GB, to create 40GB space for Ubuntu.

---

### Post by Hardhat_Harry on 2009-06-15
Well it booted into the desktop and I'm deleting all the partitions (don't need the data). I will try to boot before I install Ubuntu so I'm sure I have squished OpenSuse.

---

### Post by Hardhat_Harry on 2009-06-15
That seems to have killed it GRUB loading error 22.

---

### Post by Hardhat_Harry on 2009-06-15
Installed Ubuntu......rebooted and the screen says Grub loading error 22 and stopped.

Looks like Ive broke it

---

### Post by ugm6hr on 2009-06-15
Where did you install Grub to?

And do you have more than 1 drive plugged in?

---

### Post by pastalavista on 2009-06-15
Try the installer again, select 'manual' mode which launches the partition editor and set it up there.. be sure to create a '/' partition and you may want to make a '/home' partition to keep personal files seperate from sysyem files. makes next re-install easier

---

### Post by Hardhat_Harry on 2009-06-15
Done a dirty fix swapped the master and slave over.....I'll see if that fixes it

---

### Post by SonicSteve on 2009-06-15
> **pastalavista said:**
> Boot from the Ubuntu Live CD and select "Try without changing..." does this work? Can you load the desktop? Go to System > Administration and select partition editor. Right-click the drives and select 'unmount' and then delete the entire drive (except for partitions for dual boot, data, etc)

And then run the installer program from the desktop.

I don't think 9.04 has partition editor by default. You would have to install it into the live environment then use it.

---

### Post by ugm6hr on 2009-06-15
> **Hardhat_Harry said:**
> Done a dirty fix swapped the master and slave over.....I'll see if that fixes it

That makes sense.

You have 2 HDs.

It is likely that Ubuntu installed itself in the secondary drive, and hence the Grub entry (on the primary drive) is still looking for Suse.

---

### Post by Hardhat_Harry on 2009-06-15
Its got 5 hdd, 1 master 1 slave and a stripe set RAID. Looking at the sizes I think Ubuntu is installing itself into the RAID.

Told it to install on master now.

---

### Post by Hardhat_Harry on 2009-06-15
Nope its still not happy.

Is there a way to edit the GRUB to point the ARC path (or equivalent in Linux) to the correct disk

---

### Post by Hardhat_Harry on 2009-06-15
OK Grub says the boot record is on HD1,1 which is also the HDD I put it on so I entered grub> root (hd1,1) then grub> setup (hd1)

says its successful but still fails to boot.

I'll try again tomorrow.

---

### Post by Hardhat_Harry on 2009-06-15
Sorted it!!!

---

### Post by Miljet on 2009-06-15
It would be nice if you explain what you did to get it working. Could possibly be of benefit to others having similar problems.

---

### Post by Hardhat_Harry on 2009-06-16
It was late so I didn't post an explanation but I didn't want anyone else to spend time looking at it.

All I did was install into the partition highlighted by GRUB as the boot partition, whenever I attempted to move the boot flag to a different disk GRUB reported it as a success but the boot flag did not move even after reboots and using the SUDO command.

A bit of a dirty fix but it got me working.

---

