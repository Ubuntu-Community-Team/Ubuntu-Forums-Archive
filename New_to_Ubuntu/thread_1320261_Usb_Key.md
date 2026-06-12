---
title: "Usb Key"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Drenriza on 2009-11-09
I got a usb key in fat32 i wanna make to ntfs. How can i do this in ubuntu?.

Thanks on advance
:KS

---

### Post by nothingspecial on 2009-11-09
You either install gparted

or you ```
sudo mkfs -t ntfs /dev/sd**
```

You find out the identifier or your key by typing ```
sudo fdisk -l
```

Make sure you know for sure which it is.

---

### Post by lavinog on 2009-11-09
Disk utility should do it too.
It is pretty new, and I haven't used it to format a drive yet, but it should.

---

### Post by arochester on 2009-11-09
Use the pragram Gparted...BUT BE VERY CAREFUL WITH IT!!!

---

