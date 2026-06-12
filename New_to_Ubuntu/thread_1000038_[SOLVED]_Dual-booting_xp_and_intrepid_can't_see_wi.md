---
title: "[SOLVED] Dual-booting xp and intrepid can't see win partition"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by nfcampos on 2008-12-02
Hi,

I'm dual-booting Windows XP and Ubuntu 8.10 on a Toshiba Laptop and I'm not able to access the windows partition on ubuntu. When I had installed ubuntu I was able to acess it but now I'm not... Why?

---

### Post by uidb4056 on 2008-12-02
You can still boot on XP?

---

### Post by nfcampos on 2008-12-02
Yes.

---

### Post by nfcampos on 2008-12-02
Yes.

Sorry for the double posting.

---

### Post by Michaelg14 on 2008-12-02
One way to make it visible is to download ntfs-config from Synaptic.  Run it and it will re-write your fstab file and make your win partition visible on your desktop.

---

### Post by nfcampos on 2008-12-02
I tried what you suggested but it didn't work, it gave an error message like the one before.

Here's the error message: [IMG]http://img230.imageshack.us/img230/631/screenshottm2.png[/IMG]

---

### Post by Dj Melik on 2008-12-02
Go to command line and type:

```
sudo mount -t ntfs-3g /dev/sda1 /media/drv0 -o force
```

If that doesn't work do this:

1) Go to command line and run **blkid**.
2) Copy the UUID for /dev/sda1.
3) Go to command line and run **sudo gedit /etc/fstab**.
4) If you see a **/dev/sda1** line erase it and add the following:

```
# /dev/sda1
UUID=***********       /media/drv0       ntfs-3g         defaults      0   0
```

Just copy the UUID from earlier to *********** and save it there and restart.

---

### Post by nfcampos on 2008-12-02
It didn't work. It says "fuse:failed to acess mountpoint /media/drv0"

---

### Post by Dj Melik on 2008-12-02
> **nfcampos said:**
> It didn't work. It says "fuse:failed to acess mountpoint /media/drv0"

I just re-edited my post, try that. 

Also your error stated that "$logfile indicated an unclean shutdown." Boot into Windows and just do a clean shutdown. I'm pretty sure if you update your fstab file and do a nice clean shutdown in Windows, it should work.

---

### Post by Michaelg14 on 2008-12-02
An unclean disk is usually caused by an improper shutdown of windows or a windows crash.  (Gee that never happens)  The best way to fix it is to boot up windows and shut it down using the start menu option.

---

