---
title: "Openning Files on NTFS partition from Ubuntu aps e.g. gFTP"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by backfour94 on 2009-02-21
Hi, this is probably the sort of question that only idiots ask but I can't see how to do it.

I have installed gFTP and it shows my local drive fine, and it connects to the remote server fine.

But the files I want to use 'locally' reside on the NTFS partiton that holds by XP installation.

In Nautilus I can see this partition fine and can open files on it.

In programs such as Opera I can see the partition fine and open files on it.

But on some apps, for example gFTP, all I seem to be able to navigate around is the local Ubuntu partition.

I've tried mounting the partiton using ntfs-config but that doesn't seem to make any difference.

Any ideas welcomed, thans.

---

### Post by jerome1232 on 2009-02-21
You should be able to browse to it's mount point just like any other folder on the file system.

For example say it's mounted at /media/disk, then just point gFTP there.

---

### Post by backfour94 on 2009-02-21
So that's where it mounts it.

Thanks very much.

---

