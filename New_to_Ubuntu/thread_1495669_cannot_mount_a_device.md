---
title: "cannot mount a device"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Franz01 on 2010-05-28
I try to mount a USB disk but it operation fails... (whatever options I use)

```
root@xxx:/media# mount -t vfat -o iocharset=utf8,umask=000 /dev/sdb1 /media/usb
mount: /dev/sdb1 already mounted or /media/usb busy
```

But if I try to umount... it seems not to be mounted...

```
root@xxx:/media# umount   /media/usb
umount: /media/usb: not mounted
```

and directory has no process working on it...

```
root@xxx:/media# fuser /media/usb
root@xxx:/media#
```

How to force the opration? I ran already a lazy umount but nothig is changing...

---

### Post by -humanaut- on 2010-05-28
Have you had it plugged into any other machines where it wasn't properly unmounted if so its locked. And you'll have to plug it back into the system that locked it to unlock it.

---

