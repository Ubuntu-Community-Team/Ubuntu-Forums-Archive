---
title: "unable to mount cdrom0/ mountpoint doesn't exist"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by eimiandra on 2009-02-14
put in a dvd (can't eject it)
it's visible, but when I try to open it from the desktop I get a message that reads, "unable to mount cdrom0.  Mountpoint media/cdrom0 does not exist"

trying to open from totem media player it reads, "you are not supposed to show G_IO_ERROR_FAILED_ handled in the UI"

I tried going to terminal but that didn't get too far,
-sudo mount /dev/dvd/media/dvd
-mount: can't find /dev/dvd/media/dvd in /etc/fstab or /etc/mtab

help?


if it helps, I have a mac with intel hardware

---

### Post by bsharp on 2009-02-14
> **eimiandra said:**
> 
-sudo mount /dev/dvd/media/dvd
-mount: can't find /dev/dvd/media/dvd in /etc/fstab or /etc/mtab


Put a space in there:
```
sudo mount /dev/dvd /media/dvd
```

Also, to eject just type eject in a terminal.

---

### Post by eimiandra on 2009-02-14
still getting the same message

---

### Post by baracuda68 on 2009-02-14
I was having a /cdrom0 mounting issue recently, and I re-installed HAL with Synaptic,
Then it mounts properly.
I don't know if this is YOUR issue, but it shouldn't hurt to try...:)

---

