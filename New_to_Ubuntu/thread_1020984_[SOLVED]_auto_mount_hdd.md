---
title: "[SOLVED] auto mount hdd"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by mesmith on 2008-12-24
I have installed a second hdd.  In /media/hd2.  I can manually mount the drive via Terminal, but each time I boot the system it is unmounted.  Any way to have the drive mount automatically when I boot the system?

Mike

---

### Post by albinootje on 2008-12-24
> **mesmith said:**
> I have installed a second hdd.  In /media/hd2.  I can manually mount the drive via Terminal, but each time I boot the system it is unmounted.  Any way to have the drive mount automatically when I boot the system?

Add it to /etc/fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by dannytatom on 2008-12-24
Alternatively, you could use *Storage Device Manager*.

---

### Post by Barriehie on 2008-12-24
> **mesmith said:**
> I have installed a second hdd.  In /media/hd2.  I can manually mount the drive via Terminal, but each time I boot the system it is unmounted.  Any way to have the drive mount automatically when I boot the system?

Mike

Yes, you have to have an entry in your /etc/fstab file.  I've got my backup drive automounted and it looks like this:

```

/dev/sdb1 /home/barrie/disk ext3 rw,auto,user,exec 0 2

```There are I'm sure posts here in the forum regarding the editing of your fstab file but since I can't search while doing this here's an offsite one.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Barrie

Edit: To edit the fstab file you have to have root privelages.  If you open it w/o root privelages it will be read only in your editor.

---

### Post by mesmith on 2008-12-24
Storage Device Manager works fine.

Many thanks.

---

