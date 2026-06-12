---
title: "grub error 17 on boot"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-10-29
hi
I have googled this but not found a solution yet
I have a grub error 17 on booting
Presently I am running ubuntu off a usb and have tried the following in the terminal

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9aed9ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3742    30057583+   7  HPFS/NTFS
/dev/sda2           11628       12161     4289355   1c  Hidden W95 FAT32 (LBA)
/dev/sda3            3743       11442    61850250   83  Linux
/dev/sda4           11443       11627     1486012+   5  Extended
/dev/sda5           11443       11627     1485981   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1017 MB, 1017643008 bytes
29 heads, 60 sectors/track, 1142 cylinders
Units = cylinders of 1740 * 512 = 890880 bytes
Disk identifier: 0x0006a951

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1143      993667+   b  W95 FAT32
ubuntu@ubuntu:~$ 

I have attached a copy of gparted too
Thanks in advance

---

### Post by zvacet on 2009-10-29
I found explanation for that error [here.]("http://members.iinet.net.au/~herman546/p15.html#17")

---

### Post by kansasnoob on 2009-10-29
> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

I see from your screenshot that Gparted can't read that filesystem either, although fdisk -l shows it being Linux.

Was this just a fresh install?

---

### Post by kansasnoob on 2009-10-29
Post the output of:

```
sudo blkid
```

---

### Post by Duke Togo on 2009-10-29
ubuntu@ubuntu:~$ sudo blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="7C70309C70305ED8" LABEL="S3A2913D001" TYPE="ntfs" 
/dev/sda2: LABEL="HDDRECOVERY" UUID="1E0F-1406" TYPE="vfat" 
/dev/sda5: TYPE="swap" UUID="ab51d731-95d6-4707-8bc2-9cea3b698923" 
/dev/sdb1: UUID="98AA-0159" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="b16f03c0-7977-4318-a5b6-94399e0e03ef" TYPE="ext3" 
ubuntu@ubuntu:~$

---

### Post by louieb on 2009-10-29
Need more information or anything I could suggest would be a guess.
Is this a fresh install?
Which version (Hardy Jaunty..Karmic)?
Did it ever work?
Do you get the GRUB menu - can you boot Windows?

The fact that blkid does not show a UUID for sda3  is part of the problem. 

```

ubuntu@ubuntu:~$ sudo blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="7C70309C70305ED8" LABEL="S3A2913D001" TYPE="ntfs" 
/dev/sda2: LABEL="HDDRECOVERY" UUID="1E0F-1406" TYPE="vfat" 
/dev/sda5: TYPE="swap" UUID="ab51d731-95d6-4707-8bc2-9cea3b698923" 
/dev/sdb1: UUID="98AA-0159" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="b16f03c0-7977-4318-a5b6-94399e0e03ef" TYPE="ext3" 

```

---

### Post by screaminfakah on 2009-10-29
Sounds like Grub is broken
Google Super Grub disc.  I have used it several times to fix grub.
You can fix it from a live session but I dont remember the code.

---

### Post by zvacet on 2009-10-29
@ Duke Togo

[Reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by ranch hand on 2009-10-29
> **zvacet said:**
> @ Duke Togo

[Reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351")
This will cause nothing but grief if this is 9.10 which runs grub2.

If this is the case, do as kansasnoob askes and see the link in my sig.  there are links in it to recover grub2 and a bunch more info that you need.

If you do not know what grub you have run;
```

grub-install -v

```
Report out put.

---

### Post by kansasnoob on 2009-10-29
Since the OP stopped posting I guess we'll never know. 

They've been asked twice if this is a new install. Just need more historical info.

---

### Post by Duke Togo on 2009-10-30
sorry for the delay I`ve been away from my computer
its was an update (not to 9.10) that caused the original problem

---

### Post by Duke Togo on 2009-10-30
hi
I tried a usb version (9.10) usb creator as live session (the computer doesn`t have a cd rom)
when I type sudo grub I get the message that grub is not installed on the live session

---

### Post by Duke Togo on 2009-10-30
using a 8.04 live session

grub>find /boot/grub/stage1

error 15: file not found

---

### Post by louieb on 2009-10-30
did you use **sudo grub** to get  the grub> prompt?

Still think the fact that blkid does not show a UUID for sda3  is an indicator of a major problem. Grub can't work if there are problems accessing the Ubuntu install partition. 

It would be a good sign if you can browse the files in your hard drive install - can you? 

Need more information.  please follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")and put the results.txt file in your next post.

---

### Post by Duke Togo on 2009-10-30
after many hours research I finally found the solution
it was a large number of bad superblocks on the partition

sudo e2fsck /dev/sda3

lead to confirming block fix for over 800 blocks
followed by

sudo mount /dev/sda3 /mnt

and a reboot

hope that is of use to anyone with the same problem
and thanks to everyone who gave some advise
solved :)

---

