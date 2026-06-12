---
title: "Question about rsync"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by chrisod on 2009-05-17
I thought I had this figured out - apparently not. I used this command to copy a directory from my NAT drive to a USB drive, both mounted on Ununtu Server.

rsync -avh /mnt/photos/2008Pics /mnt/backup/Photos

I ended up with a directory /mnt/backup/Photos/2008Pics with the directory structure from the source directory and all the files as expected. I also have an empty directory corresponding to each of the directories from the source directory in /mnt/Photos

For example:

/mnt/backup/Photos/2008Pics/baseball is correct - all the files are there.

/mnt/backup/Photos/baseball is empty, and shouldn't even exist.

What did I do wrong?

---

### Post by mprince on 2009-05-17
OK one thing you might need is to add a slash at the end of the destination:

rsync -avh /mnt/photos/2008Pics **/mnt/backup/Photos/**

Also, the -m option prunes empty directories.

---

### Post by The Cog on 2009-05-17
I think I know. If you give this source:
**/mnt/photos/2008Pics**
then it copies the directory. But if you give a trailing slash:
**/mnt/photos/2008Pics/**
then it copies everything **in** the directory instead.

Ah! Beaten to it!

---

### Post by MontelEdwards on 2009-05-17
> **mprince said:**
> OK one thing you might need is to add a slash at the end of the destination:

rsync -avh /mnt/photos/2008Pics **/mnt/backup/Photos/**
That helped

---

