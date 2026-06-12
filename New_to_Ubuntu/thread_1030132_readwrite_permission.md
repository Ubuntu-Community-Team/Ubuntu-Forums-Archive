---
title: "read/write permission"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Cirabeau on 2009-01-04
I have two Ubuntu drives, one 120gb SATA, and one WD 200gb that is giving me all sorts of hell when I try to drag and drop files onto it's desktop short cut.

---

### Post by PeeZz on 2009-01-04
You have to be more precise :).

How is the WD disk connected, sata, usb, ...?
What kind of files are you copying?

How are the drives formatted? (FAT, NTFS, ext2/3/4, ...)

The more information the better we can help you!

---

### Post by mapes12 on 2009-01-04
If your drive is ext then plug it in. Then in Terminal ```
fdisk -l
``` and post the output back here.

---

### Post by Michael.Godawski on 2009-01-04
Yep,

please post the output of these terminal commands:

```
sudo fdisk -l
cat /etc/fstab
df -h
```
The terminal is in Applications > Accessories > Terminal.

---

