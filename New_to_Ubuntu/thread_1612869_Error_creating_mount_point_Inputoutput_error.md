---
title: "Error creating mount point: Input/output error"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by tame_lx_tech on 2010-11-03
Hello

I unmounted my USB hard drive with sudo umount then tried to mount it again but this error appeared

Error creating mount point: Input/output error

i couldn't find anything on this in the forum, so help would be appreciated.
drive is called WD USB 2 and normally mounts to /media

thanks

---

### Post by sikander3786 on 2010-11-03
From gparted try to run a filesystem check on your drive while it is unmounted. Alternatively you can do it from terminal. See

```
man fsck
```

for details.

You can find your desired drive by typing

```
sudo fdisk -l
```

---

### Post by Crusty Old Fart on 2010-11-03
Howdy tame_lx_tech:

External drive mount points in /media vanish when you unmount them UNLESS you create the mount point manually in /media.

Please read this thread: [http://ubuntuforums.org/showthread.php?t=1610871](http://ubuntuforums.org/showthread.php?t=1610871)

Good luck,

Crusty

---

### Post by tame_lx_tech on 2010-11-04
Hey
I turned my computer on today and it automounted, but thanks for the help :)

---

