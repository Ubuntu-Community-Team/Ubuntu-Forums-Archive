---
title: "Encrypted LVM and gparted"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by furialis on 2009-01-28
I think I made a mistake. I'm also pretty sure that you hear those words a lot on this forum. When I installed Ubuntu 8.10 I set up an encrypted LVM using the whole disk. I really was thinking that far into the future when I did it. I'd like to keep this as my main OS with all my other files and stuff, but I'd like to set up a few partitions for trying other distros. 

I get the message

The kernel is unable to re-read the partition tables on the following devices:
- /dev/mapper/b-root

I cannot edit anything. Is there a way for me to create partitions?

---

### Post by jerome1232 on 2009-01-28
As far as I know your going to have to use cli tools from a live cd. Gparted has never worked correctly with encryption or lvm for me.

If you take a look at my thread here hopefully it'll give you an idea how to work with encryption and lvm from a live desktop cd.
I wrote this while trying to figure it out under 8.04 but it should still all apply.

[http://ubuntuforums.org/showthread.php?t=940904](http://ubuntuforums.org/showthread.php?t=940904)

Fortunatly LVM is very flexible. So it's actually fairly easy to resize lvm partitions and the filesystems in them.

Unfortunately grub can't be on an encrypted partition, or one using lvm, so you have to have separate /boot partitions for each os you plan to install.

I also don't know how well luks integrates with other Linux distributions (I only use lvm not encryption)

First let's see some info about your partition setup and maybe we can help you get an idea of what to do.

Can you post the output of these commands?

```
sudo -i
fdisk -lu
vgdisplay
lvdisplay
exit
```

---

### Post by furialis on 2009-01-28
[php]
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000651c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1953022049   976510993+  83  Linux
/dev/sda2      1953022050  1953520064      249007+   5  Extended
/dev/sda5      1953022113  1953520064      248976   83  Linux
[/php]
[php]
root@b:~# vgdisplay
  --- Volume group ---
  VG Name               b
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               931.27 GB
  PE Size               4.00 MB
  Total PE              238405
  Alloc PE / Size       238405 / 931.27 GB
  Free  PE / Size       0 / 0   
  VG UUID               1lCJ5j-8pFZ-4DfE-eGIp-tBSI-8CUd-8l1Yo7
[/php]
[php]
root@b:~# lvdisplay
  --- Logical volume ---
  LV Name                /dev/b/root
  VG Name                b
  LV UUID                SKImTO-1ezI-pPnX-x6Bo-bphT-oBBi-W66uzn
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                908.60 GB
  Current LE             232602
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Name                /dev/b/swap_1
  VG Name                b
  LV UUID                GapK1X-RTyV-WK2f-eQgu-08Uo-EmYH-tyS2fy
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                22.67 GB
  Current LE             5803
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2
[/php]

Thanks for your time.

---

### Post by jerome1232 on 2009-01-28
Sorry if this is too much info at once.


so far from what I see you have

/dev/sda1 is the crypto disk and it's 931.273 GB.
/dev/sda2 is just and extended partition.
/dev/sda5 is your /boot and it's 243.14 MB.

as far as the lv's go you have

/dev/b/root which is 908.6 GB
/dev/b/swap_1 which is 22.67 MB


This is what I would do, 

[COLOR="Red"]1) backup your important data, you should keep backups on a regular basis but especially before you play with partitions.[/COLOR]

2) If you want to install Windows alongside this setup then your SOL it can't reside on a logical volume nor can it reside on a volume encrypted by luks.

3) If you want to install another Linux or BSD or similiar then I would half that boot partition, this can be done in gparted. Just open gparted, unmount /dev/sda5, and resize it. Then create another partition in there, format it as ext2 or ext3.

4) resize those logical volumes from a live desktop cd, your swap partition  is HUGE! I  would stick to 2 GB's swap at the very extreme max.

You can actually increase your file systems size while the system is running but you can't decrease them while it's online. So I'd aim small and work up as needed. I would slap that root partition all the way down to something like 20 GB's.

I like to use a data partition to store multimedia.

This should give you an idea on how to resize the filesystem and such [http://www.benkevan.com/blog/resizing-logical-volume-lvm-on-ext3/](http://www.benkevan.com/blog/resizing-logical-volume-lvm-on-ext3/)

My wife want's me to go out and eat with her so I'll be gone for awhile :)

---

### Post by jerome1232 on 2009-01-28
[http://ubuntuforums.org/showthread.php?t=950930](http://ubuntuforums.org/showthread.php?t=950930)

Here you go, Bodhi.zazen gave me alot of links to look over here. This should help you out.

---

