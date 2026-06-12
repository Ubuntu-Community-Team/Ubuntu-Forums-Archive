---
title: "Kingston Flash Drive"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by furialis on 2009-02-23
If you go to Places~>Computers, is it listed there? If it is, double click it and it should mount.

---

### Post by vanadium on 2009-02-23
The most likely cause of your USB not mounting is that it is formatted as ntfs and the file system is not clean. Have the file system checked (if ntfs, you need Windows, if fat, you can use linux "dosfsck" or Windows "chkdsk").

---

### Post by anewguy on 2009-02-23
> **vanadium said:**
> The most likely cause of your USB not mounting is that it is formatted as ntfs and the file system is not clean. Have the file system checked (if ntfs, you need Windows, if fat, you can use linux "dosfsck" or Windows "chkdsk").

And something else I've seen mentioned is to also mount it in Windows, then do an "eject" from Windows Explorer to force cache flush and re-sync of the device.  Sometimes that works as well.

As you mentioned, the file system probably isn't clean, and it can be from something as simple as removing the device in Windows without having gone through the "safely remove" stuff for USB devices.

Dave :)

---

### Post by SuperSonic4 on 2009-02-23
I suspect it's fat because I have a 2gb flash pen with kingston.

what is the output of ```
sudo fdisk -l
```

---

### Post by MrWES on 2009-02-23
> **u.lover said:**
> Hello,

I've 2GB kingston flash drive. When I inserted into USB my flash drive recognized by system but there is no icon or drive created. meanwhile i check it on windows xp system it just working fine but on ubuntu :(

From the terminal type gconf-editor and under Apps | Nautilus  | Desktop find the place to put a check mark in show volumes on desktop.

Bill

---

