---
title: "Drive won't mount"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-06-26
System specs:

Intel Core Duo 2.66GHZ
4GB RAM
Ubuntu 9.04 32 bit / Windows XP (Dual Boot w/ Grub)
2x Nvidia 8600 GeForce in SLI
nvidia driver 185.18

I have two hard drives on this system:
1. 20GB IDE drive (both operating systems reside on this disk)
2. 500GB SATA drive
The SATA has two partitions (both NTFS) I keep windows programs in one partition and Ubuntu programs in the other.

Both are internal disks.

When my system boots up I notice that the smaller IDE drive is mounted but the SATA I have to mount manually. As a total newbie I was wondering why this is.

Thanks

---

### Post by mbzn on 2009-06-26
Hi, i take it you're talking about the ntfs partition on the ide drive that would already be mounted on boot. I might be wrong but i think it's cuz grub mounts it when it loads in order for you to be able to boot windoze. the smarter people wil tell you how to automaticly unmount it when you choose ubuntu, and how to automaticly mount your other partitions on the sata drive. it would be good to know, so please considder the question asked... how do you automount ntfs partitions in linux?

Hope this helps...
Thanks

---

### Post by raymondh on 2009-06-26
I believe Ubuntu mounts partitions and not drives.  See if this link/s help

[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)
[http://scratching.psybermonkey.net/2009/05/23/ubuntu-how-to-add-or-create-hard-disk-partition-and-make-it-automatically-mount/](http://scratching.psybermonkey.net/2009/05/23/ubuntu-how-to-add-or-create-hard-disk-partition-and-make-it-automatically-mount/)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by ncc1701e on 2009-06-26
I was actually copying some files from CD to the 500GB SATA drive when my computer froze so I cold booted and ubuntu wouldn't mount the 500GB SATA drive anymore it would say to boot into windows and run chkdsk /f and so I did which solved the problem.

In my quest to migrate away from windows what if I didn't have windows on my system how would I resolve the 'unable to mount' issue?

Once again my system specs:

System specs:

Ubuntu 9.04 32 bit / Windows XP SP2 (Dual Boot w/ Grub)

Processor: Intel Core 2 Duo 2.666 MHZ (8 x333)
System Ram: 4GB RAM
Display Adapter: 2x Nvidia 8600 GeForce (512MB) in SLI (nvidia driver 185.18)

Motherboard: Abit Fatalty FP-IN9 SLI (2 PCI, 2 PCI-E x1, 2 PCI-E x16, 4 DDR2 DIMM, Audio, Gigabit LAN)
Motherboard Chipset: nVIDIA nForce 650i SLI
BIOS: Award (05/10/07)


I have two hard drives on this system, both are internal:

1. 20GB IDE drive (both operating systems reside on this disk)
    12 GB NTFS partition for windows
    8 GB partition for Ubuntu 9.04 32-bit

2. 500GB SATA drive
    120 GB NTFS partition for Ubuntu Programs
    380 GB NTFS partition for Windows Programs

---

### Post by mbzn on 2009-06-26
were you copying in linux?

if you did, did your computer respond to Ctrl+Alt+F1, where you could unmount and there would be no problem

---

### Post by ncc1701e on 2009-06-26
yes I was copying files from CD onto the smaller partition of the SATA drive I have and it just froze no mouse cursor just a dead desktop displaying so i hit the physical reset button on the front panel of my pc. then when i rebooted back into linux it would mount that sata partition any more and told me to run chkdsk /f on it before it could try to remount

by ALT-CTRL-F1 do you mean killing the x and going to cli and unmounting?

thanks.

---

