---
title: "HD mounting / partitioning"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Ow3n on 2010-10-21
I'm trying to figure out how to mount an existing RAID array as /home on a new hard drive.

I have an Ubuntu 8.04 Desktop 64 machine with a 4TB raid array. I have it partitioned as followed:

dev/sda1     ext3     /boot     200MB
dev/sda2     swap               8GB
/dev/sda3    ext3     /            4TB

I just picked up a 40 GB SSD and I'm getting ready to install Ubuntu 10.04 Desktop 64 on it. I would like to install this as the "main" drive of my machine. The goal is to use the 4TB RAID array as the /home partition. What's the best way to do that? It seems tricky because the RAID array contains the old OS.

Should I partition a /home on the SSD and then try to do some mounting wizardry to get it to use the RAID? 

How will Ubuntu know which HD to use to boot, since they're both currently labeled as /dev/sda?

Thanks!

---

### Post by Ow3n on 2010-10-21
Would it be easiest to make a symbolic link from the SSD /home folder to the RAID /home folder?

---

