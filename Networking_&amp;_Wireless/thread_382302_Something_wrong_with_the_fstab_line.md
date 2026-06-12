---
title: "Something wrong with the fstab line"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by z987k on 2007-03-11
For some reason, the network places in nautilus won't show anything, and I can't access network shares by there name, only by IP address.

So I have two network shares automounting, but only one works.

```
//192.168.1.101/SharedDocs	/media/justin	smbfs 	guest,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
//192.168.1.102/My\ Music	/media/john	smbfs	guest,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0

```

There's the fstab lines for the two of them.  However when I do a mount -a, I get "[mntent]: line 15 in /etc/fstab is bad"  This is weird, there is no difference between the first and second except they're on two different computers, so the local IP is different.

---

### Post by Mr. C. on 2007-03-11
There is a \ in one of them, but not the other.

---

### Post by z987k on 2007-03-11
correct, but that's how linux denotes a space in a filename, however I have tried it both "My\ Music" and "My Music".

---

### Post by Mr. C. on 2007-03-11
No, spaces are not represented that way for filenames.  The backslash escapes a space or special characters from the SHELL.  Pathnames in *nix do not care about spaces.

If you want to make this work, you have to replace the space char with \040, which is an octal equivalent that works with the smbmount command.

Also, use cifs instead of smbfs.

MrC

---

### Post by z987k on 2007-03-12
Thank you!  Also, what's the difference between cifs and smbfs?  Benifits/disadvantages?

---

### Post by Mr. C. on 2007-03-12
CIFS was Microsoft's somewhat failed attempt at a more common interface for a file system.  It was to supersede smbfs.  Here's a better overview:

[http://en.wikipedia.org/wiki/Server_Message_Block](http://en.wikipedia.org/wiki/Server_Message_Block)

MrC

---

### Post by dmizer on 2007-03-12
cifs will be faster and more stable than smbfs, and cifs is capable of transferring files larger than 2gb, but cifs has trouble with some nas devices.  i wrote a howto for cifs that's linked in my sig ... the fstab commands are a bit different.  but ... from looking at your fstab you've already posted, you appear to be using cifs options rather than smbfs options anyway, so simply replacing smbfs with cifs should work.

to mount your share with cifs use this command:
```
//192.168.1.102/My\040Music	/media/john	cifs	guest,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
```
the \040 denotes a space.

---

