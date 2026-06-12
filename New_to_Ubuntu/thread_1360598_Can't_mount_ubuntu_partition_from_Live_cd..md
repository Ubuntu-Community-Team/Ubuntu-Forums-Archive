---
title: "Can't mount ubuntu partition from Live cd."
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Amilo99 on 2009-12-21
When i try to mount Ubuntu 9.10 partition from Ubuntu desktop Live Cd it shows the following error 

Unable to mount location
Error mounting: mount exited with code 32: mount; wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error.

Data inside partition too important.

---

### Post by Some Penguin on 2009-12-21
fdisk -l

to list the partitions


and a mention of what command you are using for the mount might be helpful.

---

### Post by wojox on 2009-12-21
When you go to Places > Computer and open Nautilus you don't see your partition on the left and double click to mount?

---

### Post by Amilo99 on 2009-12-21
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xbb888152   
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       13969    91723117+  83  Linux
/dev/sda3           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,       
missing codepage or helper program, or other error       
In some cases useful info is found in syslog - try       
dmesg | tail  or so

---

### Post by Amilo99 on 2009-12-21
For precision i can mount xp partition.

---

### Post by Amilo99 on 2009-12-21
Nobody knows what to do in this case.every help is appreciated.

---

### Post by 73ckn797 on 2009-12-21
What are the results in terminal with:
```
sudo blkid
```?

---

### Post by anaconda on 2009-12-21
are you trying to mount ext4 partition with older ubuntu liveCD than 9.10??

The 9.10 is the first that supports ext4..  (or was it 9.04)

---

### Post by 73ckn797 on 2009-12-21
> **anaconda said:**
> are you trying to mount ext4 partition with older ubuntu livecd than 9.10??

The 9.10 is the first that supports ext4..  (or was it 9.04)
9.04

---

### Post by SecretCode on 2009-12-21
What's the result of 
```
sudo mount -t ext4 /dev/sda2 /mnt
```
?

---

### Post by maneesh77 on 2009-12-21
try this command after you are running the live CD

sudo fsck /dev/sda2

---

### Post by maneesh77 on 2009-12-21
Try using this command in terminal in live CD

sudo fsck /dev/sda2

---

### Post by Amilo99 on 2009-12-21
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1244B1E644B1CCAB" TYPE="ntfs" 
/dev/sda2: UUID="36256bb0-fb21-48d5-a96c-34ca73e2fc04" TYPE="ext4" 
/dev/sda5: UUID="555ff938-f480-4dbf-9790-0a5ef0b6bfa8" TYPE="swap"




ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Amilo99 on 2009-12-21
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

How to proceed now?

---

### Post by SecretCode on 2009-12-21
You've only mentioned accessing it from the live cd so far - can you boot the hard disk copy of Ubuntu? 

I'm starting to think this partition is corrupted.

---

### Post by Amilo99 on 2009-12-21
Yesterday into the boot screen appeared 

GRUB Loading
error : out of disk
grub rescue>

So  I have no access to ubuntu.

---

### Post by mikechant on 2009-12-21
Did your PC crash just before this problem started? Did the power go out or something?

Anyhow, it does look as if your partition is corrupt. Have you got any recent backups? If not, I've seen references to programs called testdisk and photorec. It looks as though testdisk can sometimes recover a whole corrupt partition, and photorec can recover individual files (both photos and various other file types) if the partition can't be recovered as a whole.
Have a look at this link:
[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)
and also search the forums for refs to testdisk and photorec.

I haven't used either of these myself but they look promising.

---

### Post by Amilo99 on 2009-12-21
Is there a way to save the data inside the ubuntu partition?
Can't access and can't mount it.

---

### Post by Amilo99 on 2009-12-21
I'll give a try this:
[http://www.linux.com/news/enterprise...our-hard-drive]("http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive")

Thanks everyone who helped.

---

