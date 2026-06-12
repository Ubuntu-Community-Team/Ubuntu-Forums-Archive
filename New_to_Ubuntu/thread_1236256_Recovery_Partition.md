---
title: "Recovery Partition"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Morphaeus on 2009-08-10
I recently purchased a new laptop and during the OS reconfiguration it appears I have locked myself out of the recovery partition that shipped with my computer. The partition is intact I just can't boot to it. What should the entry in /boot/grub/menu.lst look like to make GRUB boot up the recovery partition. I am using an HP Pavilion x64 system

Current menu entry

```
title		Recorvery
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1

```

I think (hope) I specified the correct partition. I also attached a screenshot of a GParted screen to give you guys an idea of what I'm dealing with. Thank you

---

### Post by lkraemer on 2009-08-10
Ah,
It appears that your Recovery Partition is the last partition that is
on the Hard Drive.  If I'm not mistaken Windows is looking for it
to be "Drive D:" (Partition #2), so it should be the second Partition.
Here is what I would try if I were in your position.  I'd purchase me
another Drive of equal size, and the same IDE or SATA interface, use
Clonezilla to copy the first partition to the new drive, followed by the
last partition.  Or copy the entire drive, and then move as needed. Then,
I'd test out those partitions to make sure everything was working
correctly.  After that I'd create the extended partition and re-install
Ubuntu on the extended Partition.  Then I'd get my hands on a Sabrent
USB to IDE/SATA interface and copy the needed data files from the
original drive to my new Ubuntu install.  Install the remaining Ubuntu
software and you should be up and running, with access to the recovery
partition.

Otherwise, you might boot Windows, go to Manage Disks, and rename/make
the Recovery Partition to D:, then move it immediately after your large
FAT32 Partition with Gparted (booted from a LiveCD), but there is always
a chance that you will/could corrupt something in the process, leaving 
you no backup.  So, I'd still like to have everything backed up first.

On a Compaq CQ60 that I purchased with Vista, I booted a Ubuntu LiveCD,
Shrank the Vista Partition, moved the Recovery partition immediatley
after the Vista Partition, and installed Ubuntu on Partiton #3, with
the last partition being Swap.  (Max of 4 Primary Partitions on any Physical
hard Drive)  I could have made the third Partition an Extended Partition
and installed Ubuntu in it as well as the Swap.

Good Luck.

lkraemer

---

