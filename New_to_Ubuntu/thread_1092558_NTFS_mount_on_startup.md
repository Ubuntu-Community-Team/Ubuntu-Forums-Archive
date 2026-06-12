---
title: "NTFS mount on startup???"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by championboxes on 2009-03-10
How would I get a partition to mount on startup??  Would I have to make a script or is there another way?  Thanks in advance

---

### Post by taurus on 2009-03-10
You would add entry in /etc/fstab for your ntfs partition if you want it to mount automatically each time you boot Ubuntu.  Install ntfs-config and use it to configure your ntfs partition then.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by finer recliner on 2009-03-10
you need to edit your fstab, for automounting

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by championboxes on 2009-03-10
ok im having a little trouble understanding what exactly I would need to put in my fstab file... Would I put ```
/dev/sda1 /media/disk ntfs defaults 1 1
``` in the file? and what should I make the last two numbers the dump and fsck options

---

### Post by colau on 2009-06-27
> **championboxes said:**
> ok im having a little trouble understanding what exactly I would need to put in my fstab file... Would I put ```
/dev/sda1 /media/disk ntfs defaults 1 1
``` in the file? and what should I make the last two numbers the dump and fsck options
[See post 10]("http://ubuntuforums.org/showthread.php?t=1168719&highlight=mount+ntfs")

---

