---
title: "syncing 2 computers with external ext3 harddrive"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by ayu on 2010-09-09
Hello,

I am currently using grsync to backup my main computer to an external HD formatted as ext3. Everything works great, as there is only 1 user there are no read/write issues.

I would now like to use that HD to sync a 2nd computer. If the external HD was FAT/etc when Ubuntu mounts it, due to the lack of file permissions in the filesystem, everything would be RW, which is good. My concern is with using ext3; user1 on computer1 might not have the same id as user2 on computer2.

Is there a way I can still use the external drive to back things up? Or do I have to make sure user1=user2? How would I do that if necessary?

Thanks in advance,
Ayu

---

### Post by seawolf167 on 2010-09-10
You are just backing up the data on each of the computers to the same external hard drive, correct? 

Provided the external hard drive has enough storage space for all the data (and noting it is ext3 formatted as you said above), just have grsync (just a gui for rsync) sync into a directory for each of the computers located on the external hard drive.


External HDD directory tree:
/computer1/
/computer2/

```
rsync -r -u -v --delete /directory_to_back_up /mount_point_of_external_hdd/external_hdd_name/computer1
```the same goes for computer 2

```
rsync -r -u -v --delete /directory_to_back_up /mount_point_of_external_hdd/external_hdd_name/computer2
```

---

