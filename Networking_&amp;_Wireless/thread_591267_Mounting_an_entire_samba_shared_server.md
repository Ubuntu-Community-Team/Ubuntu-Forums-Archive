---
title: "Mounting an entire samba shared server"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by dmonkey on 2007-10-25
Hi,

Here is the problem. I have a samba shared server, called //sambashare, for instance, and in this server are many folders:

//sambashare/folder1
//sambashare/folder2
.
.
.

I know how to mount individual folders to mount points on my U 7.10 box - not an issue. However, is it possible to mount the entire server?

Something like

mount -t smbfs -o username=?,password=? //sambashare /mnt/my_samba

?

I have tried this, and all I get is a password entry at the command line (even when specified in the command) and then an error, saying access was denied.

Any help is appreciated.

---

### Post by clee01l on 2007-10-25
Have you tried:
mount -t smbfs -o username=?,password=? //sambashare[COLOR="Red"]**/**[/COLOR] /mnt/my_samba

SInce '/' is the root folder?

---

### Post by dmonkey on 2007-10-26
Hi,

Yes, didn't work.

---

