---
title: "changing ownership/permissions in different physical drive"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2011-01-11
OKAY this is kinda embarrassing but I'm learning.
After spending days of finally getting my user data setup in it's own /home partition I have some issues with file ownership.

Specifically my data that was first backed up on a different drive (sdb as opposed to sda) has ownerships that say:

1004 -user #1004

How do I go into terminal mode and make my username the new owner of these files/folders?
I haven't figured out how to go from looking at sda to sdb in terminal. Sounds stupid I know...

Maybe I've having a SENIOR moment again.... :confused:

Ed

---

### Post by blind2314 on 2011-01-11
You don't have to "switch" between the physical disks, you just assign permissions to the mountpoint. If /dev/sdb is already mounted, then skip the next step and only do the chown shown below.
 
Mount /dev/sdb up somewhere, and then execute the following:
 
```
sudo chown -R user:group /yourmount
```

---

### Post by ozark_hillbilly on 2011-01-11
Thanks Blind!! My lightbulb just got a few watts brighter....

---

