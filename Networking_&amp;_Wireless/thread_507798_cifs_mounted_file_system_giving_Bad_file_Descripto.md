---
title: "cifs mounted file system giving Bad file Descriptor error"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by pircjo on 2007-07-23
UPDATE: apparently the problem I am describing below is not tied to the size of the filename as I had originally thought/described below, but is random instead, I tried several more copy commands and sometimes it works and sometimes it does not....

I have mounted a windows share to my UBUNTU 6.06 server via cifs and I can copy files to it. But when I try to copy a backup file that I made that is some 300 meg I have the following problem, NOTE: it only happens when I make the file name that I am copying to greater than 8 characters long and only on this (large) file, I tried it with small files with long names and no problem:

cp backup.tgz /mnt/backup_share/20070722_backup.tgz
cp: writing `/mnt/backup_share/20070722_backup.tgz': Bad file descriptor

If I use this statement all is well:
cp backup.tgz /mnt/backup_share/backup.tgz

If I try to un tar the 1st file I get an unexpected end of file message.
The physical file size when I do an ls -ls is smaller that the original backup.tgz file.

HELP!

---

