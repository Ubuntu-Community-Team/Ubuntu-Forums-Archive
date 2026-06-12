---
title: "cant find my ntfs partition with 9.10 wubi install"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by orpheusblotto on 2010-03-24
hi all.
i am trying to access files on my windows drive with karmic.
i am running a raid 0 on four sata drives. other ntfs partitions on the raid show up fine but i can't find out how to mount or otherwise access the windows ntfs partition.

any thoughts?

---

### Post by themusicalduck on 2010-03-24
Because you install with wubi, you can't access the Windows drive that wubi was installed on. Basically, Ubuntu is installed on a virtual disk drive which is stored on the NTFS partition, you can't mount that and the partition itself at the same time.

You'd either have to do a proper dedicated install onto another partition or install it onto another partition with wubi from windows.

---

### Post by garvinrick4 on 2010-03-24
> **orpheusblotto said:**
> hi all.
i am trying to access files on my windows drive with karmic.
i am running a raid 0 on four sata drives. other ntfs partitions on the raid show up fine but i can't find out how to mount or otherwise access the windows ntfs partition.

any thoughts? Open computer in Places drop down menu go to file system click on folder Host. It will show the C: drive which Wubi is a folder in. You can see the whole drive.

---

