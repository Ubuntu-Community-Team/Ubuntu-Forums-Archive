---
title: "The external hard drive is not useable after laptop come out of sleep mode"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by legolas_w on 2009-11-02
Hi
I have an external hard drive which is formatted as NTFS.
When my laptop goes to sleep mode and come out of sleep Ubuntu shows an error titled: **Unable to mount DriveB**and the content of error dialog is as follow:

```


Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc2 is already mounted on /media/DriveB
mount faile

```

To recover from this error, I should close all process which are accessing this drive and then perform the following commands:

```

sudo umount /media/DriveB
sudo mount -a

```

Is there any solution for this problem?

Thanks

---

### Post by Old *ix Geek on 2009-11-02
Let's start with the obvious: Have you done this?

```
sudo umount /media/DriveB
sudo mount -a
```

---

### Post by legolas_w on 2009-11-03
> **Old *ix Geek said:**
> Let's start with the obvious: Have you done this?

```
sudo umount /media/DriveB
sudo mount -a
```

everytime after laptop comes out of sleep I do the above command to  mount the partition again.

I think for an advanced operating system it should be automatically done instead of manuallly by the user.

Thanks

---

