---
title: "Loading failed"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Martin McFly on 2010-02-13
Hi.

I'm currently on Win XP, trying to guess how to access my Xubuntu 9.10 system. I've encountered this problem:

[http://ubuntuforums.org/showthread.php?p=8820406#post8820406](http://ubuntuforums.org/showthread.php?p=8820406#post8820406)

after selecting either normal, or recovery mode from GRUB loader and now, I'm not able to "get in". There are suggestions to run Live CD, but what should I do in it ?

If there is a way how to access my files, copy them somewhere and start fresh installation, I'm willing to do so, but I'm not sure whether I'm able to access these files from Live, or not, or if so, then how.

-Marty

---

### Post by Martin McFly on 2010-02-14
um, bump ?

---

### Post by amsterdamharu on 2010-02-14
Do you have an Ubuntu CD? If so boot from the cd and choose the try Ubuntu option, that is the live CD. You can access your files by clicking on the partition in the file explorer.

Can you copy the content of a file on your Ubuntu installation (harddisk) called fstab.

It is in %your Ubuntu partition%/etc/fsctab

Not the fstab from the livecd so not /etc/fstab.

---

### Post by Martin McFly on 2010-02-14
> **amsterdamharu said:**
> Do you have an Ubuntu CD? If so boot from the cd and choose the try Ubuntu option, that is the live CD. You can access your files by clicking on the partition in the file explorer.

Can you copy the content of a file on your Ubuntu installation (harddisk) called fstab.

It is in %your Ubuntu partition%/etc/fsctab

Not the fstab from the livecd so not /etc/fstab.

Thanks very much for reply. Yeah, I was trying to access second fstab - I do have Xubuntu CD, which should do the same job (possibly). And I suppose I should change there something, so I'll try to do it now.

Please wait ...

---

### Post by Martin McFly on 2010-02-14
```
UUID=A8FC4EC2FC4E8B10 /media/ce ntfs-3g users 0 0
UUID=190fd4d7-1ab0-463a-8ba4-98780b0c922c swap swap sw 0 0
UUID=99b6d598-9ac2-478a-beda-39428b8081a9 / ext4 users 0 1
```

Finally, I was able to mount it through Palimpsest Disk Utility and this is result.

1-old ntfs drive with XP OS, 40GB
2-swap drive my Xubuntu is using, 2.5GB
3-Xubuntu ext4 drive - bootable one --- also the one which is giving me these errors

Anything else I can do ?

---

### Post by amsterdamharu on 2010-02-14
The thread you referred to suddenly went quiet after the last post (the one before you). This could mean it was the solution.

Booting with the live cd you need to change the fstab file. Open gedit in root mode by pressing control + F2 and type gksu, in the run textfield type gedit an press Ok, type your password when asked.

Gedit is now in root mode, open the fstab file and replace the following line: 

```
UUID=99b6d598-9ac2-478a-beda-39428b8081a9 / ext4 users 0 1
```with

```
UUID=99b6d598-9ac2-478a-beda-39428b8081a9 / ext4 users**,relatime,errors=remount-ro** 0 1
```Now try to boot off your harddisk. In recovery and drop to root prompt. From there check the disk with the command fsck
[http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

---

### Post by Martin McFly on 2010-02-14
There's another problem that's keeping me busy. I don't know if it's daily use average of 16 hours last 17 months or what, but my EEE PC is going straight to hell.

Fan noise is out of control, something went wrong here and so I have to mute it to 10-20% of power, so it's not rotating so fast - not making so much noise. And Linux ext4 partition is out of order too, making hard drive go "click-click-click" noise.

And above it all, I've replaced the line and it didn't help, so I don't know, maybe I'll try to gather as much data as possible and start anew.

---

### Post by amsterdamharu on 2010-02-14
There is one more thing to try, on what harddisk and partition is your Ubuntu installed?

You can post the output of sudo fdisk -l

---

### Post by Martin McFly on 2010-02-15
Well, all these three are on one physical disk, divided into ntfs, swap and ext4 - the last one.

---

### Post by amsterdamharu on 2010-02-15
Been away for a while so could not reply, so if ubuntu is on /dev/sda3 then change this:

```
UUID=99b6d598-9ac2-478a-beda-39428b8081a9 / ext4 users,relatime,errors=remount-ro 0 1
```

to this:

```
/dev/sda3 / ext4 users,relatime,errors=remount-ro 0 1
```

---

