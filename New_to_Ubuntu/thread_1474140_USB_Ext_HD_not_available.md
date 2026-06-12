---
title: "USB Ext HD not available"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by mistypotato on 2010-05-05
I have an External USB Hard drive and I've booted into SYstemRescueCD.

The drive is there as /dev/sdb1

But I cannot find the drive in /media for example nor can I access it.

It is formatted ext4

Anyone know how I would make this drive visible to the OS for the purpose of performing a PartImage backup to it?

thx

---

### Post by mistypotato on 2010-05-06
Resolved from viewing the SystemRescueCD forum.
For the benefit of anyone else having this issue...

Since the drive WAS visible by using the blkid command (meaning the OS had recognized it), it was simply a matter of "mountng" the drive.  Here's what I followed to be able to use the drive....

[http://www.sysresccd.org/forums/viewtopic.php?f=23&t=3025&start=0]("http://www.sysresccd.org/forums/viewtopic.php?f=23&t=3025&start=0")

Here's how it should work:

1. Start up SystemRescueCd and wait for the command line.
2. Plug in your external USB hard drive.
3. Run the following command:
fsarchiver probe simple
4. Locate your external hard drive in the upper section. In the left ("DISK") column it should have an entry like "sda" or "sdb".
5. Assuming your external hard drive was listed as "sdb", run the following command:
mount -t ntfs-3g /dev/sdb1 /mnt/backup
Your external hard drive should be accessible and writable in the directory "/mnt/backup" now.
6. Do your desired backup with partimage. Tell partimage to save the image somewhere on "/mnt/backup/"!
7. After you have finished backing up everything you want, run the following two commands:
umount /mnt/backup
sync
8. Unplug your external USB hard drive.

That's it. You can shut down SystemRescueCd now if you want with:
shutdown -h 0

Hope that helps.
eomanis

---

### Post by mistypotato on 2010-05-06
Important Note if you are trying to use PartImage to backup a Linux system....

PartImage (as of 05/05/2010) cannot backup a Linux system utilizing an Ext4 partition.

The latest versions of Ubuntu (9 .x and 10.x) use Ext4 partitions so PartImage will not work on these new versions of Ubuntu at the time of this post.

I'm now downloading CloneZilla to give that a try...will let you know how CloneZilla goes....

---

