---
title: "is there any way to chmod a folder, no longer have access to owner user account?"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by Lkm on 2011-06-30
My ubuntu broke a couple days ago and I've rendered it unfixable; updating through the live CD, dpkg and failsafeX don't work, so I've decided I'll call it a day and start over.

The problem is I have certain folders which I have permissions owner-only, so I cannot copy them anywhere else or even read them. Is there any way to get around linux's annoyingly secure permissions at all? (Or mount the drive under windows?)

---

### Post by dFlyer on 2011-06-30
First you can't mount them under windows as it doesn't know how to read ext4 fs. Have you tried to use sudo to copy the file, or even:

sudo chown name:name file or directory name.    you will have to replace name:name with your user name..

---

### Post by Lkm on 2011-06-30
Thank you! :D

---

### Post by fabricator4 on 2011-06-30
> **dFlyer said:**
> First you can't mount them under windows as it doesn't know how to read ext4 fs. 

You can indeed mount ext4 partitions as ext2 under Windows.  All you need is the ext2 windows [driver from Sourceforge]("http://sourceforge.net/projects/ext2fsd/").

It works great.  Note that when you have an ext4 partition mounted as ext2 you have no journaling, but it works fine because ext4 partitions are fully backwards compatible.

The Ext2fsd driver makes life so simple if you have a mix of Windows and Linux partitions and a need to use Windows - no more USB pendrive transfers.  Highly Recommended.  Note that the default setup is to mount Ext2 drives as read-only.  This can be changed in the configuration for each partition.

Chris.

---

### Post by wildmanne39 on 2011-06-30
> **Lkm said:**
> My ubuntu broke a couple days ago and I've rendered it unfixable; updating through the live CD, dpkg and failsafeX don't work, so I've decided I'll call it a day and start over.

The problem is I have certain folders which I have permissions owner-only, so I cannot copy them anywhere else or even read them. Is there any way to get around linux's annoyingly secure permissions at all? (Or mount the drive under windows?)
Hi, also you can get to your files with the livecd here are the instructions for having root access.
```
sudo -i nautilus
```
opens the root file browser window in the live cd, no password required.

---

### Post by Lkm on 2011-07-01
I made another partition for backup, 'chown'ed home, mounted all relevant drives and copied files over, leaving ubuntu section ready for reinstall.

Thanks!

---

