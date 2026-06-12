---
title: "Resized/moved partition and destroyed MBR by mistake..."
date: 2009-06-09
forum: New to Ubuntu
---

### Post by dreadh3ad on 2009-06-09
Earlier today I added space onto my windows partition and moved the ubuntu swap partition with gparted livecd.  Upon rebooting grub gave me Error 22.

I loaded up the ubuntu 8.10 live cd and attempted to find grub with 

```
find /boot/grub/stage1

and
find /grub/stage1


```

Unfortunately this yielded nothing.

I attempted to boot into the ubuntu partition manually with the gparted live cd but this did not work.  I was able to boot into my windows partition.

What did I do?

---

### Post by lindsay7 on 2009-06-09
Do you have more than one hard drive?

Also, you should type sudo grub and then the commands you showed.

---

### Post by dreadh3ad on 2009-06-09
No I only have one hard drive.

My apologies for not including it but i did launch grub with

```
sudo grub
```

---

### Post by lindsay7 on 2009-06-10
Try typing fdisk -l (the letter l), and post the results. I am a little confused by this,

> I attempted to boot into the ubuntu partition manually with the gparted live cd but this did not work. I was able to boot into my windows partition.


When you say boot into, do you mean look at or start up?

---

### Post by dreadh3ad on 2009-06-15
Sorry for the late reply I have been working crazy hours the past week.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6456    51857788+   7  HPFS/NTFS
/dev/sda2            6457        6716     2088450   82  Linux swap / Solaris
/dev/sda4            6717       19452   102301920   83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    c  W95 FAT32 (LBA)

```

I did this using the ubuntu 8.10 live disk.  The live disk recognizes and mounts the partition containing the installed version of ubuntu 8.10 but I do not have the permissions to view it.  I have attempted to start up ubuntu 8.10 with gparted live cd option: Boot into Partition.  This has enabled me to start up windows xp.

---

### Post by iponeverything on 2009-06-15
In the live CD.

open a terminal and run:

```

sudo bash
mount /dev/sda4 /mnt
grub-install --root-directory=/mnt /dev/sda

```

---

### Post by dreadh3ad on 2009-06-15
When I rebooted my machine I was stuck at a grub prompt.

```
ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# mount /dev/sda4 /mnt
root@ubuntu:~# grub-install --root-directory=/mnt /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
```

---

### Post by iponeverything on 2009-06-15
ok.. 

from the grub prompt:

```

root (hd0,3)
find /boot/grub/stage1
setup (hd0)

```
then type quite and reboot

---

### Post by iponeverything on 2009-06-15
what happens when you just type "boot" from the grub prompt?

---

### Post by dreadh3ad on 2009-06-16
I followed those directions only to return to the grub prompt.

---

### Post by Sjeti on 2009-06-16
> root (hd0,3)

It would be 2, because its zero based. (/dev/sda3 = hd0,2)

What might be your issue is your menu.lst is calling the wrong sections to boot from.

For your setup your /boot/grub/menu.list entry should look something like this:

title		Ubuntu 9.04, 2.6.28-11
root		(hd0,2)
kernel		/vmlinuz-2.6.28-11-generic root=/dev/sda3 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

Thats what I'm running.  You could also look up your UUIDs and place them such:

title		Ubuntu 9.04, 2.6.28-11
UUID		(UUID for /dev/sda3)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=(UUID here) ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

---

### Post by john wagner on 2009-06-16
Must have been the weekend for doing this...  I did it Friday to my Dapper.  Error 22.  Tried all the suggestions above, and then some.  With the live cd, I could run Dapper, but not get my system to find my HD/OS at all.  Tried SuperGrub, everything. 

Nada.

I was just fortunate to have been at the point where I had been thinking of moving up in the OS's of ubuntu.  So I reformated with Jaunty, reloaded what backups I had (external HD, last backup in Feb...YIKES! :( ).

Jaunty is right out of the box, love it.

john

---

### Post by iponeverything on 2009-06-16
was there any output from the commands?

It starting to look to me like your partition table might be a little funky.

---

### Post by Sjeti on 2009-06-16
You should check into making a separate home partition, it makes reinstallation a breeze.

---

### Post by iponeverything on 2009-06-16
> **Sjeti said:**
> It would be 2, because its zero based. (/dev/sda3 = hd0,2) 

Thanks Sjeti that is good thing elaborate on since many over look it.. I did have it covered though as shown from his partition table.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6456    51857788+   7  HPFS/NTFS
/dev/sda2            6457        6716     2088450   82  Linux swap / Solaris
/dev/sda4            6717       19452   102301920   83  Linux

```

---

