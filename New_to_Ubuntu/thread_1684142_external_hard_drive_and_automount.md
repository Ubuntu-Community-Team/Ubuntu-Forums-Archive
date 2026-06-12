---
title: "external hard drive and automount"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by col48 on 2011-02-08
I have just bought an external hard drive.

Session 1:
I reformatted it to ext3 using mkfs.
I then had to add a line to /etc/fstab and create a mount point in /media to get it to mount.
I then copied come files across to it satisfactorily.
I then umounted it and disconnected it and logged off

Session 2:
ubuntu tried to automount the external drive.

I don't want this to happen: I want to it to mount automatically when the drive is plugged in part-way through a session, but not to try to mount when it isn't.

How do I do this?  

The additional line in fstab I cloned from the entry for an internal hdd - maybe that's the problem?  I added it at the bottom and it looks like this:

```
/dev/sdd1       /media/ExternalDrive  ext3 relatime,errors=remount-ro 0       1
r
```

---

### Post by cariboo on 2011-02-08
Remove it from /etc/fstab, you don't need it there. The drive will automount when you plug it in

---

### Post by col48 on 2011-02-09
Thanks. I'll do that.

How does it know where to mount it?

---

