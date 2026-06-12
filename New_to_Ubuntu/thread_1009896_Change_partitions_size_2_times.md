---
title: "Change partitions size 2 times"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by slamdunk on 2008-12-13
Hi,

I would like ask you if it's possible make this kind of change in my partitions:

At moment in my hard disk:

First 30 Giga Vista
Remaining part Ubuntu

so:

30 G Vista | Ubuntu root partition | swap partition | Ubuntu home partition

I would like remove completely Vista and so enlarge before root partition and then reduce it to enlarge home partition. Is it possible?

Thanks,
julio

---

### Post by Paqman on 2008-12-13
Yes, although it might take quite a long time. Deleting partitions is quick, but moving and expanding existing ones is very slow.

Depending on your computer it might just be quicker to back up your /home partition and reinstall to some nice newly-made partitions.

---

### Post by vanadium on 2008-12-13
Quicker, and easier. What you want to do is possible but will also require you to to some manual adjustments to grub and /etc/fstab. Not that difficult, but already rather technical nevertheless.

Alternatively, you might just reformat the Windows partition to a 30 GB ext3 partition for additional data storage. This is safest and easiest.

---

### Post by Keith Hedger on 2008-12-13
If you are going to change your ubuntu partitions dont forget you must boot from a live CD or similar as you cant change a partition thats in use.

---

### Post by caljohnsmith on 2008-12-13
You can save yourself from having to modify your /etc/fstab and /boot/grub/menu.lst if you save a copy of your original UUIDs of the partitions, and then after you are done partitioning and the UUIDs have changed, you can simply change them back to what they were originally. To see the UUIDs, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo blkid
```
And then once you are done with the partitioning, you can change the UUIDs back by copying/pasting their original values into the following commands:
```
sudo swapoff -a
sudo mkswap -U "[COLOR="Blue"]<original UUID>[/COLOR]" /dev/[COLOR="Blue"]sdXY[/COLOR]
sudo tune2fs -U "[COLOR="Blue"]<original UUID>[/COLOR]" /dev/[COLOR="Blue"]sdXY[/COLOR]
```
So for your root and home partitions, you would use the "tune2fs" command above to change their UUIDs, and for the swap partition you would use the "mkswap" command. That will save you from having to change any of your system files to correct for different UUIDs. Let us know how it goes. :)

---

### Post by CatKiller on 2008-12-13
> **Keith Hedger said:**
> If you are going to change your ubuntu partitions dont forget you must boot from a live CD or similar as you cant change a partition thats in use.

You'll also need to turn swap off, even running from the live cd, since you'd need to move that partition too.

```
sudo swapoff -a
```

I'd probably be tempted by the re-install route, too, but caljohnsmith's suggestion is an intriguing one, though.

---

### Post by slamdunk on 2008-12-14
Thanks for replies

I try to resume steps:

1) Run Ubuntu 8.10 Live CD
2) Run shell
3) Run "sudo blkid" and save informations in anyplace
4) Use partition program of the live-cd and delete Vista partition and "enlarge" root partition
5) sudo swapoff -a; sudo mkswap -U "<original UUID>" /dev/sdXY; sudo tune2fs -U "<original UUID>" /dev/sdXY (for my root and home partitions)
6) Re-run "sudo blkid" and save informations
7) Always with partition program "shrink" root partition and enlarge home partition
8) sudo swapoff -a; sudo mkswap -U "<original UUID>" /dev/sdXY; sudo tune2fs -U "<original UUID>" /dev/sdXY (for my root and home partitions)

Is it correct?

Thanks,
Julio

---

### Post by vanadium on 2008-12-14
You might want to post the output of "sudo fdisk -l" here so we can see what your current partitioning looks like. It really will depend on your current situation.

In any case, moving a partition is a rather slow and risky operation, and better avoided if there are other acceptable options.

---

### Post by slamdunk on 2008-12-15
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+   6  FAT16
/dev/sda2              15        1320    10485760    7  HPFS/NTFS
/dev/sda3   *        1320        3810    20000000    7  HPFS/NTFS
/dev/sda4            3811       19458   125685168+   f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6            3811        5633    14643216   83  Linux
/dev/sda7            5634        5757      995998+  82  Linux swap / Solaris
/dev/sda8            5758       19130   107418591   83  Linux

Partition table entries are not in disk order

----

thanks,
julio

---

### Post by vanadium on 2008-12-16
You referred to one Vista partition, but I see two ntfs partitions, sda2 and sda3. Both are primary partitions.

sda6 is probably your /, sda7 is your swap and /sda8 is probably your/home. There is a small sda5 that probably is not used.

I think that doing a clean install including repartitioning the whole drive would be the best thing to do.

Alternatively, you might do the following quite easily and fast (although it is not anymore absolute beginners stuff).

(1) Delete sda3, enlarge sda2 to fill the space of sda3, format it in ext3 as an additional data partition
(2) Delete sda5. Increase sda6 to take the (few) space that was occupied by sda5.

This would clean up, but there are complications that make this operation exceed the absolute beginners level. The device designations of your / and /home will change, and the UUID of your /home will change. The reference to the root partition for grub will also change.

You might consider to omit (2), which results in only a minor space gain anyway. Device designations then would not change. However, references of grub to the boot partition would still be affected.

To achieve fully what you want means moving the root in one way or another (partition moving or cloning it with a dd command then reuse the clone, ... These are lengthy operations that are nice if you are a hobbyist, want to take the challenge and spend the time and effort. In all other cases, backing up your data and reinstalling your entire system is by far the preferred option.

---

### Post by slamdunk on 2008-12-16
yes, effectively I have more "ntfs" partitions. They were included by Dell for "quick restore" of the main Vista's partition. However I think it's useless spend too much time playing with partitions. I'll save content of my home, re-format all hard disk and reinstall ubuntu.

thanks for explaining (they helped me to choose)

julio

---

