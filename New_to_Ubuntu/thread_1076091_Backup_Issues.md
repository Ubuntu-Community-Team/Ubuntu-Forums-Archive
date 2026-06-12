---
title: "Backup Issues"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by theozzlives on 2009-02-21
I enter the following:
```
sudo tar cvpzf ozzie-laptop.tgz --exclude=/proc --exclude=/lost+found --exclude=/home/backup.tgz --exclude=/mnt --exclude=/sys  --exclude=/home/ozzie/E-Books  --exclude=/home/ozzie/Music  --exclude=/home/ozzie/porn  --exclude=/home/ozzie/VirtualBox --exclude=/windows /

```
and get:
> tar: Error exit delayed from previous  errors

Why?  I get a 1.6 GB  file.

---

### Post by theozzlives on 2009-02-21
bump

---

### Post by kellemes on 2009-02-22
Add this to your command and see what's in it..
```
--exclude=backup.log > ~/backup.log
```
As far as I know it's a non critical error, you have your tarball.
Still you want to know what's going on, so watch the output in ~/backup.log

---

