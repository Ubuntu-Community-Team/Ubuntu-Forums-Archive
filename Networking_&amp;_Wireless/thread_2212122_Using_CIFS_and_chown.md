---
title: "Using CIFS and chown"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by cranerja on 2014-03-19
I'm trying to mount my network drive in /networkdrive. In fstab, I'm using the line "//192.168.0.13/share    /networkdrive   cifs    guest,uid=1000,iocharset=utf8   0       0".
 I'm the only user that can create and delete inside this folder. How do I make it so all users have full access? I've been looking but nothing seems to work.

---

### Post by Morbius1 on 2014-03-19
It's sort of kind of like mounting an ntfs partition.

Change this:
> //192.168.0.13/share    /networkdrive   cifs    guest,uid=1000,iocharset=utf8   0       0
To this:
>  //192.168.0.13/share    /networkdrive   cifs    guest,uid=1000[COLOR=#0000cd]**,dir_mode=0777,file_mode=0666,nounix,**[/COLOR]iocharset=utf8   0       0

Then unmount the share:
```
sudo umount /networkdrive
```
And remount it with this which will check for syntax errors and if there are none mount it:
```
sudo mount -a
```

---

### Post by cranerja on 2014-03-29
This worked perfectly. Thank you!

---

