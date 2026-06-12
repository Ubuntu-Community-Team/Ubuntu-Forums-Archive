---
title: "Do I _really_ need Samba/smb4k ?"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-11-15
I installed Samba and smb4k sometime ago, as I needed to copy files from Ubuntu to another HDD on the same computer. That HDD had Win XP on it.

Now all I need to do is to access (read/view) some of those files. Do I still need Samba/smb4k to do that, or can I uninstall both of them, and still be able to mount/access the files on the other HDD ?

Oygle

---

### Post by Iowan on 2008-11-15
I'm not familiar with smb4k. My feeling is (been wrong before) if you want to access files on NTFS, you'll probably want to leave (at least) Samba installed.

---

### Post by oygle on 2008-11-16
Okay thanks, I'd better leave it as it is then.

---

### Post by oygle on 2008-11-20
I had a look on another computer that is running Hardy, as it can access the partitions on a Win XP HDD okay. Then compared the packages on both, and realised I don't need the following, if all I want to do is view/access the files.

samba
smb4k
smbfs
winbind

all that is needed (if you don't need write permissions, etc) are:

samba-common
smbclient

HTH

Oygle

---

