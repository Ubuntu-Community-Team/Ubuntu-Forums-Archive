---
title: "Permissions and ownership"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by mlempenau on 2011-01-13
I set up my ubuntu with two accounts, both admin.  One was named admin and the other mike.  I then had something happen and lost the use of mike.  I made a new admin account and named it mikee.  This worked until I deleted the mike account.  Then many of my files refused to be editable.  Also my directories.  I noticed that they all have permissions grayed out and in red letters it says root.  I tried changing permissions, groups.  No work.  So instead of sudo I tried su.  Still no help.  What should I do?

---

### Post by vanadium on 2011-01-13
What is your output of the command "groups"?

---

### Post by mlempenau on 2011-01-14
Sorry for being late.  

output of groups:

mikee adm dialout fax cdrom floppy tape audio dip backup video plugdev fuse lpadmin netdev admin sambashare libvirtd vboxusers mike administrator
mikee@mike-desktop:~$

---

### Post by zeroseven0183 on 2011-01-14
.

---

### Post by zeroseven0183 on 2011-01-14
Hi mlempenau.

You can determine whose files are still "owned" by the old account by typing ```
ls -l <directory path>
```

See if those are still owned by "mike mike". If they are, you can change their permissions to "mike" by
```
sudo chown mikee:mikee <directory path>/*
```

And by that asterisk, I mean, everything under that directory.

---

### Post by bilkay on 2011-01-14
If you want to change all files owned by mike in a directory tree to being owned by mikee, the following will work:

$ cd <directory>
$ sudo find . -user mike -exec chown mikee:mikee {} \;

---

### Post by mlempenau on 2011-01-14
Ok, before I do something stupid ... 

mikee@mike-desktop:/media/sdb4$ ls -l /media/sdb4/
total 320
drwxr-xr-x 59 root root 16384 2010-11-19 15:20 Documents
drwxr-xr-x  3 root root 16384 2010-10-16 07:54 Firefox Documentation
drwxr-xr-x  4 root root 16384 2010-10-03 16:11 GPS
drwxr-xr-x 56 root root 16384 2011-01-07 20:11 ipodlib
drwxr-xr-x  4 root root 32768 2010-11-03 14:11 jynon
drwxr-xr-x  2 root root 16384 2010-11-23 15:42 MAGICDVDCOPY_TEMP
drwxr-xr-x  2 root root 16384 2010-10-15 11:34 misc photos
drwxr-xr-x  2 root root 16384 2010-12-17 23:02 Movies
drwxr-xr-x  3 root root 16384 2010-10-03 16:11 mp3
drwxr-xr-x  3 root root 16384 2010-10-08 20:19 My Zinio Library
drwxr-xr-x 76 root root 16384 2010-12-18 16:29 Pictures
drwxr-xr-x  2 root root 16384 2010-12-29 12:52 ppts
drwxr-xr-x  2 root root 16384 2010-10-10 14:28 Recycled
drwxr-xr-x  3 root root 16384 2010-10-07 11:53 System Volume Information
drwxr-xr-x  2 root root 16384 2010-10-16 20:37 Thai language
drwxr-xr-x  8 root root 16384 2010-10-14 14:43 Ubuntu Documentation
drwxr-xr-x 12 root root 16384 2010-10-03 16:11 USB1 (F)
drwxr-xr-x  8 root root 16384 2010-10-03 16:11 USB2 (G)
drwxr-xr-x  4 root root 16384 2010-10-15 11:45 VCD Movies

Everything is owned by root.  What should I do?  Do I have to us "su"?

---

### Post by vanadium on 2011-01-14
How is this drive formatted? Is this an external drive or an internal drive? How is it mounted?

You won't be able to change permissions if the file system does not support linux file permission. Automatically mounted external drives should by default be writable for the user who plugged it in.

You can reveal the file systems with the command "sudo blkid".

---

### Post by mlempenau on 2011-01-14
Drive is FAT32, external and the question that broke the ice ... Its auto mounted by Storage Device Manager.  I just loaded it to auto mount and forgot that it needs instruction on how to mount.  Oh me...  Thanks all for the help.  The old man's memory strikes again!

---

