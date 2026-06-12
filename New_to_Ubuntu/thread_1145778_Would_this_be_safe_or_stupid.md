---
title: "Would this be safe or stupid?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Gforce20 on 2009-05-01
I installed Ubuntu 9.04 on my external hard drive and used the entire disk as ext4 (except for swap). Would it be safe to re-partition the drive to make an NTFS section? The disk is 250 GB, and if I could use 125 of those with Windows, that'd be great. Right now Ubuntu is taking up about 40 GB, but I don't know if resizing the partition would cut off some files or not. Any tips would be great.

---

### Post by lucasl on 2009-05-01
It doesn't matter anyway, because you're carefully backing up your data... right?
You can definately resize it and files will be moved so they don't get cut off. You can't resize your root drive that the computer is running on though (because it is mounted), so you'll need to get a [Live CD with GParted on it]("http://gparted.sourceforge.net/livecd.php"), boot that and resize from there.

---

### Post by jbrown96 on 2009-05-01
It's always recommended to backup any important files first. That being said, I've never lost any files changing the size of a partition. 

Boot from the LiveCD. In System--->Admin--->Partition Editor you will be able to shrink the Linux partition. It's also recommended that you create the NTFS parition here as well. You never know when Windows will get gready and repartition the entire disk.

---

