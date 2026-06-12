---
title: "fstab entry"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by scambro on 2010-02-20
I just re-installed my image of ubuntu, now on 9.10.  I have a RAID5 (4.5TB) attached.  If I do not mount the image in fstab, and instead just mount using the GUI when it starts up, it seems perfectly fine.  When using the following fstab entry, I'm getting a read-only system:

```
UUID=887b0f65-c91e-44b4-840b-2a3af21cc019 /media/FourFive ext4    defaults,errors=remount-ro  0  0
```

I created the /media/FourFive directory as such:
```
$ ls -all /media/
total 16
drwxr-xr-x  4 root root 4096 2010-02-20 16:01 .
drwxr-xr-x 21 root root 4096 2010-02-20 15:44 ..
lrwxrwxrwx  1 root root    6 2010-02-20 12:07 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2010-02-20 12:07 cdrom0
drwxrwxrwx  9 root root 4096 2009-08-30 13:26 FourFive

```

In my /var/log/messages, I see this:

```
Feb 20 16:00:48  kernel: [   13.427833] EXT4-fs (sdb1): barriers enabled
Feb 20 16:00:48  kernel: [   13.444790] kjournald2 starting: pid 965, dev sdb1:8, commit interval 5 seconds
Feb 20 16:00:48  kernel: [   13.444811] EXT4-fs (sdb1): warning: mounting fs with errors, running e2fsck is recomm$
Feb 20 16:00:48  kernel: [   13.481094] EXT4-fs (sdb1): internal journal on sdb1:8
Feb 20 16:00:48  kernel: [   13.481102] EXT4-fs (sdb1): delayed allocation enabled
Feb 20 16:00:48  kernel: [   13.489718] EXT4-fs: mballoc enabled
Feb 20 16:00:48  kernel: [   13.489745] EXT4-fs (sdb1): mounted filesystem with ordered data mode
```

Is there something I'm missing in the fstab entry?  Seems correct to me, but it's been awhile since I set this up before.  Also, I don't want to run e2fsck because I have data on this device right?  Thanks!

---

### Post by falconindy on 2010-02-20
Presumably you're not mounting it manually with '-o errors=remount-ro', so that's where the difference comes in. You should run fsck on the array and see if that fixes anything. If not, you may have a problem with one of the members of the array.

---

### Post by scambro on 2010-02-20
> **falconindy said:**
> Presumably you're not mounting it manually with '-o errors=remount-ro', so that's where the difference comes in. You should run fsck on the array and see if that fixes anything. If not, you may have a problem with one of the members of the array.

Makes sense...  Running fsck now.  I imagine this will take awhile on 3+TB of data :)

---

