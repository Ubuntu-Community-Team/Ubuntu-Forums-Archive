---
title: "Installing Ubuntu 9.10"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by daveritah on 2010-02-24
I am attempting to install Ubuntu 9.10 with a dual boot. When the partioner page came up, it ask if I would like to dual boot, but also wanted to partion the drive. I have already created a seperate partion for Ubuntu to load into, but when I selected manual, and then the partion I created, it posted a message, that no root directory was found. How do I direct Ubuntu to load into this new partion and yet allow a dual boot on startup.

---

### Post by Fougner on 2010-02-24
Have some free space, or a new clean partition. Choose "manual partition", and edit your empty partition, dedicated for your ubuntu install.
Now choose / for mountpoint and choose your filesystem, preferably Ext3/4.. Finished =)

---

### Post by J V on 2010-02-24
Yeah, if you expected it to run on ntfs you will need to reformat that particular partition ;)

---

### Post by daveritah on 2010-02-24
how do I reformat that partion?

---

### Post by 3rdalbum on 2010-02-24
> **daveritah said:**
> how do I reformat that partion?

Select it and click Edit. Change the filesystem type to "ext3" or "ext4" (either one is okay) and tick the "Format this partition" checkbox. Your main Ubuntu partition needs to have the mountpoint as "/", so set this in the Edit window.

To clarify, this is done from the "manual partitioning" screen of the installer.

---

### Post by thegod_slayer on 2010-02-24
if the partition has some data on it that you don't want to lose 
then just right click on the partition and click change....
this will allow you to make partitions for your swap and your / 
without losing your data.
if you want to use the full partition regardless of losing data in it....
then delete the partition..... after which you will see the size of the partition as free space on the partition table.
now right click on the free space and click on add.
then enter your swap area size (which is double of your ram) in mb
then the size for / partition.

now install and enjoy.:KS:KS

---

### Post by 3rdalbum on 2010-02-24
> **thegod_slayer said:**
> if the partition has some data on it that you don't want to lose 
then just right click on the partition and click change....
this will allow you to make partitions for your swap and your / 
without losing your data.

True, but you can't change the partition type without also formatting. Ubuntu requires an Ext, JFS, XFS or Reiser partition, so if your partition is NOT one of those formats then you need to change the partition type.

And if you're doing ANYTHING in a partitioner you should already have your data backed up anyway. I can't stress this enough - even nondestructive operations can go wrong once in a while.

---

### Post by thegod_slayer on 2010-02-24
> **3rdalbum said:**
> True, but you can't change the partition type without also formatting. Ubuntu requires an Ext, JFS, XFS or Reiser partition, so if your partition is NOT one of those formats then you need to change the partition type.

.
yeah correct, i forgot to mention that.........
that can be done by selecting ext4 or ext3 type file system from the drop down list box in the partitioner page.:D:D

---

### Post by daveritah on 2010-02-24
Thanks for your help everyone, will try it again - Dave

---

