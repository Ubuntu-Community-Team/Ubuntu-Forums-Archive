---
title: "Dual boot system, booting problem."
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Tnoty on 2010-02-27
Help,
I had a dual boot system running XP and Ubuntu. Everything was running fine until I had to reinstall my XP partition for a class project.  Now I can't dual boot anymore.  The Ubuntu partition is still on the hard drive, but I'm unable to boot to it.  Do I have to reinstall my Ubuntu partition or is there some other fix.  Thanks.

---

### Post by Tnoty on 2010-02-27
> **Tnoty said:**
> Help,
I had a dual boot system running XP and Ubuntu. Everything was running fine until I had to reinstall my XP partition for a class project.  Now I can't dual boot anymore.  The Ubuntu partition is still on the hard drive, but I'm unable to boot to it.  Do I have to reinstall my Ubuntu partition or is there some other fix.  Thanks.


Ok I think I know what the problem is.  I've been told that when I re-installed my XP partition it probably knocked out or over-wrote my grub boot sector. Now I need to know how to re-install my grub.  I have the Ubuntu disc if necessary.

---

### Post by sandyd on 2010-02-27
for ubuntu 9.10
boot up from livecd.
```

sudo fdisk -l
```
note your ubuntu partition (partition should be something like /dev/sdax)
Below, replace /dev/sdax with the ubuntu partition
then
```

sudo mount -t ext4 */dev/sdax* /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
sudo grub-install /dev/sda
sudo update-grub
exit

```

```

sudo shutdown 0 -r
```

---

### Post by GSF1200S on 2010-02-27
> **Tnoty said:**
> Ok I think I know what the problem is.  I've been told that when I re-installed my XP partition it probably knocked out or over-wrote my grub boot sector. Now I need to know how to re-install my grub.  I have the Ubuntu disc if necessary.

Good job ;) and im going to help you do so. For the OP, I need to know what version of ubuntu you are running. The earlier versions use grub-legacy, where the newer version uses grub2.

I will help you if you run into trouble, but this community page has a fantastic description that should get your ubuntu back:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It tells you all the steps one by one to get things working.

---

### Post by GSF1200S on 2010-02-27
> **carlee said:**
> for ubuntu 9.10
boot up from livecd.
```

sudo fdisk -l
```
note your ubuntu partition (partition should be something like /dev/sdax)
Below, replace /dev/sdax with the ubuntu partition
then
```

sudo mount -t ext4 */dev/sdax* /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
sudo grub-install /dev/sda
sudo update-grub
exit

```

```

sudo shutdown 0 -r
```

Haha, I beat you to it on the last thread- you beat me to it this time.
To the OP: you can follow my link or follow carlee's instructions.

---

### Post by sandyd on 2010-02-27
> **GSF1200S said:**
> Haha, I beat you to it on the last thread- you beat me to it this time.
To the OP: you can follow my link or follow carlee's instructions.

:lolflag:
those instructions are imbeded in my head by now :D
however, grub-legacy has dissapeared from my brain...

---

