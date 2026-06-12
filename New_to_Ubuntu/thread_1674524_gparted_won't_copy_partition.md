---
title: "gparted won't copy partition"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by skypuppy on 2011-01-24
In moving a previous disk contents from a larger sata disk to a smaller ide disk (vista) I'm having trouble.  There are two partitions on the original disk.  part 1 size is 900+gb while part 2 size is around 14 gb.  The computer that used that disk had a malfunction on the sata hardware and nothing sata will work on it anymore.  
So in a live system recovery cd I bring up gparted.  Setting partitions on the smaller disk works fine as does formatting them.  
I can copy the contents of the smaller partitions from the old disk to the new one just fine.  Their partition sizes are similar.
I cannot copy the contents of the 900+ gb partition from the old drive to the newer 500gb partition no matter what I try.  It just grays out the "paste" function and won't let me do it.
I thought of shrinking the 900+ partition size down to, say 300+ so that the original partition will be smaller than the target but I'm concerned with data loss and I can't figure out a way to back up that original partition in case something goes awry.

Any ideas, please?

---

### Post by Sleven7 on 2011-01-24
> The computer that used that disk had a malfunction

If the drive is on another computer now, open your File Browser and copy & paste the files from the old to the new.

---

### Post by fabricator4 on 2011-01-24
...and if the new machine is a windows machine as it seems to be, just install extFS using [this procedure]("http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html") so it can read the ext partition and copy the files wherever you want them.

Chris

---

### Post by skypuppy on 2011-01-24
This has  nothing to do with Winblows.  I'm operating entirely in Ubuntu Linux 10.10.  Or I can boot using a linux 'system recovery cd' with gparted on it.

What I have to do here is move the two vista partitions from the 1 tb sata disk onto a 500 gb ide disk.  I can't boot into vista at all like it is.  I could "borrow" an xp machine but why would I want to do that?  Winblows has nothing like gparted in the public domain.

Why won't gparted copy the 900 gb partition onto the 500 gb partition (both boot partitions, btw)?

---

### Post by fabricator4 on 2011-01-24
> **skypuppy said:**
> Why won't gparted copy the 900 gb partition onto the 500 gb partition (both boot partitions, btw)?

Probably because it thinks it won't fit.  You could resize the partition to the same size or smaller if the data is less than 500Mb, which may take some time, or you can mount the windows partition in Linux and just copy the data across with Nautilus, or the CP command.

In a terminal window:

```

sudo fdisk -l

```

to get fdisk to list all partitions it can find.  Generally, sda will be the first hard drive in the system and sdb will be the second.  The partitions will be sdb1, sdb2 and so on. The system partition type will give a good clue as to which are the windows partitions, and the size in cylinders will show which are the big and the little partitions. 

Now, make a directory in your home folder and mount the partion you want to use to it

```

mkdir ~/tempdir
sudo mount /dev/sdbx ~/tempdir

```

where sdbx is the partition that you want to mount.

Now, when you look in the folder ~/tempdir you will be looking at the windows partition.

This use of mount relies on it being able to autodetect an NTFS or FAT partition, which should work, but if it fails that will be why.

Once you are finished you can unmount the partition ready to mount the second one to the same directory (or a different directory if you wish)

sudo umount ~/tempdir


Hope that's all clear enough.

Chris

---

