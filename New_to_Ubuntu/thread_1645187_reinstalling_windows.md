---
title: "reinstalling windows"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by arju305 on 2010-12-14
guys after reinstalling windows , i couldnt find my grub. I inserted a live cd  but the cd doesnot show any of my hard disk drives. How can i recover it.
Thanking you in advance.

---

### Post by arju305 on 2010-12-14
output of $fdisk -l

omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe1b6e1b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5043    40507866    7  HPFS/NTFS
/dev/sda2            5044       60801   447875617+   f  W95 Ext'd (LBA)
/dev/sda3            7681       12748    40708678+   7  HPFS/NTFS
/dev/sda5            5044        5354     2494464   82  Linux swap / Solaris
/dev/sda6            5354        7680    18684928   83  Linux
/dev/sda7           12749       25496   102398278+   7  HPFS/NTFS
/dev/sda8           25497       60801   283587381    7  HPFS/NTFS

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders
Units = cylinders of 2250 * 512 = 1152000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x59da59da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           4        3487     3917824    b  W95 FAT32

---

### Post by Rubi1200 on 2010-12-14
If Ubuntu was booting normally before you reinstalled Windows, then it is simply a case of reinstalling the GRUB bootloader.

From a LiveCD, run the following commands:
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```Don't forget to take the CD out when rebooting.

Back in Ubuntu, run this command to pick up the Windows install.

```
sudo update-grub
```

Just to play safe, before you run these commands.

Post the results of the boot info script linked at the bottom of my post please.

---

### Post by arju305 on 2010-12-14
> **Rubi1200 said:**
> If Ubuntu was booting normally before you reinstalled Windows, then it is simply a case of reinstalling the GRUB bootloader.

From a LiveCD, run the following commands:
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```Don't forget to take the CD out when rebooting.

Back in Ubuntu, run this command to pick up the Windows install.

```
sudo update-grub
```Just to play safe, before you run these commands.

Post the results of the boot info script linked at the bottom of my post please.

ruby .... when i enter this command....... 
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
The file /mnt//boot/grub/stage1 not read correctly.


**************************************
Help me please.............

---

### Post by Rubi1200 on 2010-12-14
Hi,
please run the boot info script linked at the bottom of my post.

There are instructions included.

Post the results back here.

Thanks.

---

### Post by arju305 on 2010-12-14
> **Rubi1200 said:**
> Hi,
please run the boot info script linked at the bottom of my post.

There are instructions included.

Post the results back here.

Thanks.






Thanks alot..... It worked...........

---

### Post by Rubi1200 on 2010-12-14
Okay...but how?

In any event, I see you marked this as Solved which is always good news.

You are more than welcome by the way :)

---

### Post by arju305 on 2010-12-15
> **Rubi1200 said:**
> Okay...but how?

In any event, I see you marked this as Solved which is always good news.

You are more than welcome by the way :)
The commands u told woked.... thanks.......

---

