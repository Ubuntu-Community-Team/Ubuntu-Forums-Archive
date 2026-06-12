---
title: "Duel Boot partitions"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Nemix on 2008-12-13
i really dont have a clue what im doing lol =P
so im on the Preparing Partitions section, i take it because i want to duel boot i need to do select manual. I read i need to right click and press Resize to reduce the size of my windows partition, but i only get these options:
-Edit Partition
-Delete Partition
-----------------------
-Undo changes to partitions

i have two partitions already:
/dev/sda1 ntfs (C: drive)
/dev/sda2 ntfs (recovery, default from HP)


im really not sure how to continue, ive read the Partitioning your disks in Ubuntu Documentations.

---

### Post by tomtom1982 on 2008-12-13
First alternative is you take first point of partition dialog an let the installer resize your Windows partition (if there is enough free space).

Second alternative is you take the live cd, start gparted, resize your recovery partition, with the won place you create 3 new partitions: one ext3-partition (mountpoint /) up to 20 GB, a second ext3-partition (mountpoint /home) for your documents and one SWAP-partition (as big as RAM x2).

You also can make a Recovery-CD out of the recovery-data using nLite(Win2000,XP) or vLite(Vista) and format your recovery partition.

Please also read this: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Nemix on 2008-12-13
ok so, if i want to do the first one i should go back and select "Guided-resize SCSI3...." (below it it there is a a box saying winows vista/longhorn (loader) 58% 129.2GB and another box with Ubuntu 8.10 42% 94.8GB)

and that should auto resize my partitions? 

and thanks for a speedy reply :KS

oh i see now u added a link THANKS!

---

### Post by tomtom1982 on 2008-12-13
Yes, that option will auto resize your partitions.

Made it dozen times on dozen PCs without errors.

It will create a partition with mountpoint / and a SWAP. There won't be a seperate /home-partition but seperate /home-partition is not absolutely neccesary.

---

### Post by Nemix on 2008-12-13
hmmm weird, while it was resizing it encountered a problem and then put me into manual mode...:confused:

ill see if i can do it manually.

---

### Post by adult swim on 2008-12-13
if it fails when you do it manually, you may need to boot windows and defragment your hard drive for it to work.  make sure and not install on your ntfs partition :)

---

### Post by tomtom1982 on 2008-12-13
And like the link on my first post says:

It's never wrong to back up your files ):P

And if nothing of this works for you, you also can try wubi for installing Ubuntu inside Windows.

---

### Post by blackened on 2008-12-13
It might be a good idea to use the Vista disk management tool to shrink your Windows partition before doing the install. I've run into alot less problems following this method. Also, as adult swim already mentioned, it's important that you defrag the Windows partition first.

---

### Post by Nemix on 2008-12-13
ok i think probably cos i forgot to defrag before installing.
got myself a nice long wait for defrag to be completed.

but i really do appreciate all your help :KS:KS

---

