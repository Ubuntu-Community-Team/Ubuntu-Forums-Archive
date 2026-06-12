---
title: "need terminal commands to format drive plz"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by drillerccg on 2010-07-02
Hi,

new to Linux and am trying to use fdisk to format my USB pendrive (16GB).

All I need are the commands to format a partition to:

1- FAT32 format
2- Ext2/3/4 format
3-FAT16 format

TIA

PS No luck with gparted. Too many errors.

---

### Post by Rubi1200 on 2010-07-02
What types of errors are you getting with GParted? 

Did you run GParted from the LiveCD (the recommended method for using it) and try to format the USB stick that way?

---

### Post by nothingspecial on 2010-07-02
```
sudo mkfs -t vfat /dev/sd??
sudo mkfs -t ext3 /dev/sd??
```

```
man mkfs
```

Make sure you understand what you are doing before you do it so you don`t format the wrong thing.

---

### Post by drillerccg on 2010-07-02
@Rubi1200 Gparted was giving me problems running it from the hard drive. Took the hard drive out and ran it with a live CD and everything appeared to be OK. However, I am still not able to make 4 different partitions( fat32, ?, /home, swap) on a USB stick and install Ubuntu on the / partition.

@nothingspecial thanks for the warning. I'm new to Linux but can follow detection not to mess things up too much;).

Doesn't the code for Fat 32 have to have the FAT version in it? What is the difference between what you wrote and this: (sorry couldn't find insert code function)

sudo mkfs.vfat -F 32 -n "label" /dev/sdX1

TIA

PS Here is the post on what I have been trying to do but not that successful:

[http://ubuntuforums.org/showthread.php?p=9538158#post9538158](http://ubuntuforums.org/showthread.php?p=9538158#post9538158)

---

### Post by allCuExpMa on 2013-02-03
the right command is:

mkdosfs -F32 -v -n "LABEL" /dev/sd?

best of luck
T[m]

---

### Post by sffvba[e0rt on 2013-02-03
*Old thread **closed**.*


404

---

