---
title: "no user access to new partition"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by nVee on 2009-11-25
Hey

I just partitioned and formatted a new hard drive in my ubuntu desktop 9.10 using GParted. All tasks we're completed successfully, and I have clicked on Places > Mount 500 GB filesystem and it mounted the drive.

The problem is, I cannot do anything to it. I cannot create folders or anything? Is there something I must set or how does this work?

When I right click on the drive > properties > Permissions > I get an error saying the permissions for "lots of codes" could not be determined.

---

### Post by Mr. Devil on 2009-11-25
```
 
sudo chown -R user:group /data

```
 
Replace user:group with your username/group and change the partition mount point.

---

### Post by ukripper on 2009-11-25
can you post output of these commands so we can have look how you formated it and which filesystem you are using

```
sudo fdisk -l
```

```
mount
```

---

