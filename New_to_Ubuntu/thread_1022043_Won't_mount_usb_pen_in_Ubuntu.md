---
title: "Won't mount usb pen in Ubuntu"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by ArnsteinK on 2008-12-26
This is what it says: 

mount: wrong fs type, bad option, bad superlock

What should I do?

---

### Post by taurus on 2008-12-26
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ArnsteinK on 2008-12-26
Disk /dev/sdb: 8032 MB, 8032092160 bytes
131 heads, 50 sectors/track, 2395 cylinders
Units = cylinders of 6550 * 512 = 3353600 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        2396     7839744    b  W95 FAT32

---

### Post by taurus on 2008-12-26
Try something like

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by ArnsteinK on 2008-12-26
Thanks, it worked :D

---

