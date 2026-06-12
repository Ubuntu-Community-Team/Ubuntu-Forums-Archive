---
title: "Unable to mount directory with CIFS"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by txr13 on 2007-11-17
When mounting a Windows shared directory to the local filesystem using smbfs, the mount succeeds, but listing the directory says "Permission denied". Doing an ls on the parent directory reveals the mount directory is listed with entirely unknown permissions (something like ?----------).

After doing some research, I found that I need to use cifs to resolve this issue. However, attempting to mount via cifs returns the error:
```
mount error 20 = Not a directory
```

I would greatly appreciate some help with this!

---

### Post by Grundlefleck on 2008-05-11
This worked for me, hopefully it will work for you to: in the fstab file, or from the command line, add the option "nounix". 

My entire fstab line for my NAS drive looks like this:
//192.168.1.69/public /media/Storage/	cifs	rw,nounix,guest,iocharset=utf8, 0 0

(of course, if you've got a credentials files, or any other options just keep them in)

Please let me know if this works for you.

    Grundlefleck

---

