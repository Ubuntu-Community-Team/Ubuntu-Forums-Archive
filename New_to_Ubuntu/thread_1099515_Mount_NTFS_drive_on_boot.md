---
title: "Mount NTFS drive on boot"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-18
I have two physical internal HDDs, sda and sdb - sda had Windows on it and sdb is a media disk with photos/videos and music.

I just installed Ubuntu 8.10 on sda, formatted the Windows partition and all so now Windows is gone for good. It's formatted as EXT3. My "media disk" is still NTFS. It shows up under "Places" and when I click on it it mounts itself and is fine, but how do I tell Ubuntu to mount this drive every time I boot up?

It's located under /media/Media Disk

Thankyou!

---

### Post by taurus on 2009-03-18
Install ntfs-config and use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by humphreybc on 2009-03-18
See I already have that and when I run it all I get is a window that says:

> 
Enable write support for internal device

Enable write support for external device


The first one is greyed out and the box is unchecked, the second one the box is checked.

---

### Post by taurus on 2009-03-18
Try to unmount that ntfs partition first.

---

### Post by humphreybc on 2009-03-18
> **taurus said:**
> Try to unmount that ntfs partition first.

Thanks that worked a charm. :)

---

