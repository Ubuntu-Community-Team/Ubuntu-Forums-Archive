---
title: "SCSI3 or SCSI5?"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Fishhooker on 2009-02-07
All right. I've got a Toshiba Satellite X205-SLi6, with two physical hard drives. I've been using Windows Vista ever since I got this computer; all of my data is on C:, and I plan to install Ubuntu Studio 8.10 on D:.

I go to the partitioning menu, and I select "Guided: Use Entire Disk," and that's when it all goes pear shaped. It shows me two options that I've never seen before:

SCSI3 (0,0,0) (sda)
SCSI5 (0,0,0) (sdb)

Which one of these translates to C:, and which translates to D: ?

---

### Post by blueridgedog on 2009-02-07
Perhaps if you looked at your disks, the partitions on them would give you a hint.  From a terminal, you can run the command:

```
sudo fdisk -l
```

---

