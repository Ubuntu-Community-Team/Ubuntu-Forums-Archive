---
title: "Command to write to samba share"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by dje on 2007-08-31
I can write to a samba share folder using nautilus and in the address bar the directory is:

smb://sharecomputer/sharefolder

how could i send a compressed folder (backup) from my hard drive to the share folder using the command line? thanks in advance :)

---

### Post by kidders on 2007-09-01
Hi there,

You can't. You'll need to mount the share first, before anything other than Gnome can access it.

---

### Post by bubbalouie on 2007-09-03
You can use **smbclient**

The following post may help :) :

[http://ubuntuforums.org/showthread.php?t=318010&highlight=samba+backup](http://ubuntuforums.org/showthread.php?t=318010&highlight=samba+backup)

---

