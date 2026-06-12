---
title: "Live usb: no space left"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by the.bn on 2010-11-16
Hi!
In persistent mode my Ubuntu live reports something like:

mounting aufs on /root: no space left
(initramfs)

There is only a busybox and  few available commands :confused:
How can I solve?

Thanks :P

---

### Post by C.S.Cameron on 2010-11-17
Rule # 1:
Don't run update on a persistent USB.

If you need to recover anything valuable from your casper-rw persistence file you can loop mount it:

> sudo mount -o loop casper-rw /media/casper/

If there is nothing valuable on it you can download a new casper-rw file from pendrivelinux.com or just reinstall to pendrive using usb-creator.

If you want more persistence than 4GB, (the limit for a FAT32 file), you can create a partition and name it casper-rw then add persistent to the text.cfg file:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by the.bn on 2010-11-17
Hi and thank you @C.S.Cameron! :)

Yes, i must recover some important files from my Ubuntu persistent usb.


So...now i have: 1 netbook (without cdrom and without hdd) and 1 usb pendrive and 1 O.S.: ubuntu live (only in ram and not in persistent mode).
The hard disk is gone (smart status:disk failure is imminent) with a lot of errors.

Ubuntu in live mode below:

```
ubuntu@ubuntu:~$ sudo mount -o loop casper-rw /media/casper/ 
casper-rw: No such file or directory

```

Note: I used this software: "Linux Live USB Creator" from Windows for creation of my ubuntu usb.
But now, where is casper-rw in my usb pendrive??
And is possible mount image (casper-rw) with this live usb pendrive or i must use also another pendrive?

Thanks for your help and sorry for my bad english :)

---

### Post by C.S.Cameron on 2010-11-17
You can find casper-rw in the root of the pendrive.
I think you can only access it when booted from another drive.

[http://ubuntuforums.org/showthread.php?t=1028564](http://ubuntuforums.org/showthread.php?t=1028564)

---

