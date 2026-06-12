---
title: "Can't mount external"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by cartisdm on 2009-02-16
For some reason I can't ever seem to mount my 500gb USB external harddrive.  I get this error (look at screenshot).  After I mess around with the suggestions in the "Details" of the error I can get it to mount but I never remember what I have to do.  Plus, it's really annoying that I have to do this.  Why can't I just plug it in and mount it?


EDIT:  I tried adding ```
/dev/sdc1	/media/Big\/Max	ntfs-3g force 0 0
``` to the fstab file but then when I try to mount I get an error saying I don't have permission

---

### Post by cartisdm on 2009-02-16
Fixed it.  For other users that run into this problem I had to install NTFS support using the following code:

```
sudo apt-get install ntfs-config
```

That should fix any problems you have!

---

### Post by cariboo on 2009-02-16
If you have a dual boot system, I would boot in to Windows and unmount your drive properly. It is that or do as the error message suggests and use the force mount option. You have to type it exactly as it says in the error message:

```
sudo mount -t ntfs-3g /dev/sdc1 /media/Big\Max -o force
```

The way to stop getting this error is to umount the drive properly all the time. When using Windows use the Safley Remove option, and in Ubuntu right click on the drive icon and select umount volume.

Jim

---

