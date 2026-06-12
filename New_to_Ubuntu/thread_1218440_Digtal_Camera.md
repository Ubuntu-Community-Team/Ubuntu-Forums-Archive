---
title: "Digtal Camera"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by mar2000 on 2009-07-20
I remember when Ubuntu used to mount my digital camera like any USB flash drive. Now, when I mount it, it is located at:

gphoto2://[usb:002,005]/

I have no idea where that is in the file system. I just wish I knew how to get it to mount it in /media like it used to.

Also, every time I plug in the camera this way, it will freeze X.org for about a minute before I can even browse the photos.

---

### Post by The Cog on 2009-07-20
Maybe this will help:
[http://ubuntuforums.org/showpost.php?p=7205851&postcount=4](http://ubuntuforums.org/showpost.php?p=7205851&postcount=4)

---

### Post by mar2000 on 2009-07-24
Thank you so much, this works so much better. That was what I was looking for.

---

### Post by LewRockwell on 2009-07-24
> **The Cog said:**
> **Camera doesn't mount when connected and switched on.**

Many people have reported this bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281)

**Quick fix:**
Use the command:```
sudo killall gvfs-gphoto2-volume-monitor
```

then connect the camera.

**Long-term fix:**
Prevent the process from starting. Use the command:```
sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
```



.

---

