---
title: "gparted not working"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Alex-H on 2009-05-25
Hi all. I used easeus partition manager in windows to free up some space from the fat32 partition xp is using, and headed back to xubuntu (9.04) to try to claim the resulting free space for ext2. Fired up gparted and got 'scanning /dev/sda partitions' for three hours, disk thrashing at 100% the whole time.

fdisk reports this:
```

alex@tinylaptop:~$ sudo fdisk -l
[sudo] password for alex: 

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda0376c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         261     2096451    b  W95 FAT32
/dev/sda2   *         262        1739    11872035    b  W95 FAT32
/dev/sda3            2996        3057      498015   82  Linux swap / Solaris
/dev/sda4            3058        3648     4747207+  83  Linux
alex@tinylaptop:~$ 

```

I'm using an old JVC laptop, mp-xp7210, it's a p3-800 with 256mb and 30gb hdd, no floppy or optical drives.

Thanks for any pointers,
Alex

---

### Post by raymondh on 2009-05-25
> **Alex-H said:**
>  disk thrashing at 100% the whole time.
I'm using an old JVC laptop, mp-xp7210, it's a p3-800 with 256mb and 30gb hdd, no floppy or optical drives.


Hello Alex,

Booting and running the ubuntu, is the disk still trashing?  Or  did it trash/grind only when you ran gparted?

Back-up/save your files somewhere else first :)

Regards,

---

### Post by Alex-H on 2009-05-30
Aside from the other issue about the update manager that I recently posted in another thread, the machine runs just fine - a real performance boost over the xp it was running. Gparted definitely caused the disk to thrash for ages, possibly because I have no idea about how to partition a disk, and now have four primary partitions on it...

---

### Post by b@sh_n3rd on 2009-05-30
My favourite part in installing *Ubuntu* of all OSes is the partitioning part of it :D. Ubuntu, coz it's got a diverse list of File Systems and the partitioning method is awfully cool..Anyways, since I really like partitioning, I tend to become kind of a perfectionist at this point...that's bad though...:D

About your problem, firstly, to reclaim any space onto your Xubuntu install, try the LiveCD. Any partition you edit should be unmounted. Since your installed system can't function without a partition, you'll have to use the LiveCD. As I understood, you edited your partition with a separate Disk Partitioner? That shouldn't cause any problem I think as you only *resized* a partition. If you use a different partitioning program, in most cases your PC might not be able to detect it, but this is not true for all computers. I say this by experience (don't get scared about this though. As it is, it works on your PC). Try the LiveCD anyways and tell me how it goes...

---

### Post by Alex-H on 2009-05-30
No dice :(

There's no removeable media drive in this machine at all, it has only usb 1 ports and can *only* be persuaded to boot from a usb floppy when all goes pear shaped - i have tried at some considerable length to make it boot from usb stick or cd.

---

### Post by NHArticleTen on 2009-05-30
try gparted via Puppy Linux Live USB on a thumb drive?

---

### Post by Alex-H on 2009-06-01
Haven't been able to boot anything at all from a thumb drive, not even a 1.44mb dos 6 image supposedly presenting itself as a floppy (real usb floppy did work)...

Is there like a 'safe mode' or comparable that i could reach from hdd boot?

---

### Post by Alex-H on 2009-06-01
Haven't been able to boot anything at all from a thumb drive, not even a 1.44mb dos 6 image supposedly presenting itself as a floppy (real usb floppy did work)...

Is there like a 'safe mode' or comparable that i could reach from hdd boot?

---

### Post by LewRockwell on 2009-06-01
how was the original/current operating system installed?

---

### Post by mikechant on 2009-06-01
> Gparted definitely caused the disk to thrash for ages, possibly because I have no idea about how to partition a disk, and now have four primary partitions on it...

What you did seems reasonable, and there's nothing wrong with having four primary partitions as such (not so good for future expansion, but it's a perfectly valid partition set up).

The only thing I can think of is that "easeus partition manager" which you mention has done something strange. One thing you could try is going back to windows and undoing the change you made with this software. Then see if gparted will run OK. If that's OK, then gparted is quite capable of shrinking the FAT32 partition. 

However, that's when it gets a bit tricky. Normally at this point you could boot from the liveCD/USB, turn the swap off in gparted, delete and recreate the swap partition at the start of the free space, then expand the ubuntu root partition to the new end of the swap partition. You'd end up with the same sequence of partitions as you started with but with sda2 smaller and sda4 larger.
But if you can't run from a liveCD/USB then the ubuntu root partition will be mounted and you won't be able to do anything with it.
However, as I think someone else mentioned, in that case how did you install ubuntu in the first place if not from CD/USB?

There are ways to get around the root partition being mounted and no live/CD/USB support but it's not worth going into them until you've answered the install question.

---

### Post by Alex-H on 2009-06-02
wubi or something like it, I can't remember which one ultimately worked. Transpired one had a setting marked 'my computer cant  boot from cd'.

---

