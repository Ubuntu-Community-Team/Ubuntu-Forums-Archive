---
title: "Extended Partitions"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-06-05
Hey everyone. I'm about to embark on my first PC build (as soon as I can order the parts), and I'm thinking ahead to partitioning my hard drive.

It's 750GB, so I'm going to say 700GB formatted. I plan on dual booting Windows 7 RC 64-bit (until it's officially released) and Ubuntu 9.04 64-bit.

I want a separate data partition however.

Since you can only have three primary partitions, I was thinking about this setup:

partition 1 (primary partition 1) = 300 GB NTFS [C:\ (Windows 7)]
partition 2 (extended partition of 1) = 350 GB NTFS [D:\ (data)]
partition 3 (primary partition 2) = 42 GB ext4 [sda4 or whatever (/)]
partition 4 (extended partition of 3) = 8 GB swap [swap]

Now, if I formatted partition 1 in October (when Windows 7 is officially released), will that wreck the extended partition? I'd like to keep one primary partition available just in case. If it will wreck my data partition, then I guess I'll just make it its own primary.

Thanks ;)

---

### Post by CatKiller on 2009-06-05
You can only have one extended partition. You can have many partitions inside that extended partition. So you may want two primary partitions (Windows and Data) and an extended partition that contains your / and swap partitions.

If you re-install Windows you'll probably have to re-install GRUB, since Windows is pretty certain to trash it and replace it with Windows' own bootloader.

---

### Post by Lazy-buntu on 2009-06-05
Oh, kind of off topic, but I have another question: if I set up ubuntu to be an SSH server, will I be able to access other partitions (like the data partition--NTFS) or just my ext4 partition?

---

### Post by Lazy-buntu on 2009-06-05
> **CatKiller said:**
> You can only have one extended partition. You can have many partitions inside that extended partition. So you may want two primary partitions (Windows and Data) and an extended partition that contains your / and swap partitions.

If you re-install Windows you'll probably have to re-install GRUB, since Windows is pretty certain to trash it and replace it with Windows' own bootloader.

I see. So partition 1 = Windows, Partition 2 = Data, Partition 3 = Extended partition.

Partitions inside the extended partition could be /, swap, and another data partition?

And you can format the sub partitions within the extended partition without touching the others inside it?

---

### Post by CatKiller on 2009-06-05
> **Lazy-buntu said:**
> Oh, kind of off topic, but I have another question: if I set up ubuntu to be an SSH server, will I be able to access other partitions (like the data partition--NTFS) or just my ext4 partition?

You can access any mounted partition by navigating to the mount point. cd /mnt/data, say.

> **Lazy-buntu said:**
> I see. So partition 1 = Windows, Partition 2 = Data, Partition 3 = Extended partition.

Partitions inside the extended partition could be /, swap, and another data partition?

And you can format the sub partitions within the extended partition without touching the others inside it?

That's right. Just don't remove the extended partition itself unless you really want to. Bootloaders lie outside of the partitions, in the Master Boot Record, so they can be messed up by fiddling with the partitions, but it's easy enough to re-install GRUB to the MBR from the live disk if that happens. But other than that it's all quite straightforward as long as you don't do anything too hastily. And backups are always handy to guard against those "actually, no, I didn't want to format that partition" moments.

---

### Post by Lazy-buntu on 2009-06-05
> **CatKiller said:**
> You can access any mounted partition by navigating to the mount point. cd /mnt/data, say.



That's right. Just don't remove the extended partition itself unless you really want to. Bootloaders lie outside of the partitions, in the Master Boot Record, so they can be messed up by fiddling with the partitions, but it's easy enough to re-install GRUB to the MBR from the live disk if that happens. But other than that it's all quite straightforward as long as you don't do anything too hastily. And backups are always handy to guard against those "actually, no, I didn't want to format that partition" moments.

Thanks a lot! I'm ready to order my parts, if only my deposit from earlier would clear!

---

### Post by LewRockwell on 2009-06-05
you may only have 4 primary partitions maximum, or 1-3 primary and 1 extended.

for example:
I've got your 750GB hard drive(700GB formatted).
I'm going to create a 25GB primary partition for windoze OS formated ntfs
I'm going to create a 5GB swap partition
I'm going to create a 20GB Linux partition
I'm going to create a 650GB Extended partition
I'm going to create a 100GB logical partition formatted ntfs for data

the other 550GB in the extended partition will remain unallocated for now and I can do anything I want with it later

sometimes I create logical partitions to use as targets for back-up clones of my active partitions(while still doing complete disk clones to an external hard drive as a secure back-up)

(and, yes you can put OSes on your logical partitions and have grub pointing to them)

---

### Post by bodhi.zazen on 2009-06-05
See also :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

