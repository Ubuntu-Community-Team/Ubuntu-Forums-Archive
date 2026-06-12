---
title: "Unable to access partition"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by bobheaps on 2011-03-30
I was running windows7 and Ubuntu 10.04 on the same hard drive. When I installed Ubuntu I put /home on a separate partition. Due to my tinkering where I shouldn't I could not boot. I re-installed windows from a backup OK but I could not rescue the Ubuntu system (it was corrupted).I re-installed the Ubuntu system, no separate partition for /home, thinking I could use the existing. However, the install placed a /home folder on the partition with the system, but I cannot access the original /home. fdisk says it is there, so how can I mount it to access it?

---

### Post by blind2314 on 2011-03-30
Well, if it's still there (and assuming not corrupted), this will get it for you.
 
```
mkdir /oldhome
mount -t ext4 /dev/sdxx /oldhome
```
 
Replace ext4 with ext3, depending on your filesystem needs, and replace /dev/sdxx with your actual partition (i.e., /dev/sda1, /dev/sdb1, etc).

---

### Post by seawolf167 on 2011-03-30
If you need to find the drive labeling for the previous post to work, use the command

```
sudo fdisk -l
```

then look for the appropriate entry

---

