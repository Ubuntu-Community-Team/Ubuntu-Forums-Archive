---
title: "USB Help please"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by mosnazz on 2009-11-03
i recently installed ubuntu 9.10 on my lenovo idea pad s10 using a 8gb flash/thumb drive. now i cannot mount the flash drive on my desktop which is also running ubuntu.  I used synaptic to download Gpart, but i still cant get the USB Thumb drive to mount even after reformating to ext2-ext3 and even fat32. i get a system message that says my desktop does not support the fat32 file system.  im a complete rookie, please be kind!

---

### Post by ukripper on 2009-11-03
> **mosnazz said:**
> i recently installed ubuntu 9.10 on my lenovo idea pad s10 using a 8gb flash/thumb drive. now i cannot mount the flash drive on my desktop which is also running ubuntu.  I used synaptic to download Gpart, but i still cant get the USB Thumb drive to mount even after reformating to ext2-ext3 and even fat32. i get a system message that says my desktop does not support the fat32 file system.  im a complete rookie, please be kind!

post output of the following commands, you can copy paste them in terminal:
```
lsusb
```

```
sudo fdisk -l
```
```
blkid
```

---

