---
title: "recovering data from deleted partition"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by oaridus on 2010-05-16
Hi, I was trying to delete a logical drive in windows xp and the damn disk management tool in windows not only deleted my other windows partition but also my linux /data ext3 partition. Now I have a unallocated space in place of these partitions. The data is still there but the entries in the partition table have been removed. So how do I recover my partition. I was trying to use the following tutorial.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

I used the
 sudo parted /dev/sda    -- and then
 rescue START END command and could get back the /data partition. But it gives me the following error while mounting the partition.

mount: wrong fs type, bad option, bad superblock on /dev/sda7, missing codepage or helper program or other error. In some cases useful info is found in syslog - try dmesg | tail or so.

What does this mean. How to I fix this? Also when I try to recover my windows partition using parted it scans for a while and then does nothing. It doesnot ask for writing the lost partition in the partition table. What do I do? Please help.

---

### Post by oldfred on 2010-05-16
I have these links to related issues:

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by brennydoogles on 2010-05-16
TestDisk/PhotoRec will be the way to go. Install it with
```
sudo aptitude install testdisk
```

and then run:

```
sudo testdisk
```

It will run you through recovering the partition. Hope that helps!

---

### Post by bumanie on 2010-05-16
I too would try testdisk - look [here]("http://www.cgsecurity.org/wiki/TestDisk") and [here]("http://members.iinet.net.au/~herman546/p21.html") for tutorials

---

### Post by oaridus on 2010-05-17
That worked !!!! thanks a lot. It is a great program. I started the program using ./testdisk_static in the linux folder of the testdisk and then after analysis it showed me my partitions. I changed all deleted to logical (which was the case before) and then asked it to write the entries. And wholla it worked!!! My system is back to the old state.

---

