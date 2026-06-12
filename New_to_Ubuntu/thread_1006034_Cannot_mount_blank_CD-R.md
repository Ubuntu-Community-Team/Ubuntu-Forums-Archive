---
title: "Cannot mount blank CD-R"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by amazingtaters on 2008-12-08
Just like the title says. My fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=13955dc2-772c-4447-80ef-24667b0f104a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=97690122-62a0-46df-b8b1-858b9a9044d2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

when I try to *sudo mount /media/cdrom0* I get the following error
mount: special device /dev/scd0 does not exist

anyone know what to do about this?

---

### Post by handydan918 on 2008-12-08
I don't think you can do anything about not being able to mount a non-existent file system.

What are you trying to do?

---

### Post by amazingtaters on 2008-12-08
Okay, what happens is, I pop a blank CD into my laptop's DVD drive and absolutely nothing happens.

---

### Post by psusi on 2008-12-08
If the cd is blank it kind of means there is nothing there TO mount, but it looks like your problem is you have no cd drive ( at least not that the OS can see ).  Do you not have a cdrom item in your places menu?

---

### Post by egalvan on 2008-12-08
OK, I popped a blank CD into the drive,
 and an icon popped up on the desktop with the title:

"Blank CD-R Disc"

I opened the drive, and the icon disappeared.

Hardy 8.04.1

---

### Post by JoshuaRL on 2008-12-08
I've had a problem like this.  When blank media is in the drive, the drive doesn't mount.  I think that's because there is nothing to mount.  The hardware is still there, but there's no data to mount into the filesystem.  But can you open Brasero and burn off a CD anyway?  The system should recognise that it's a blank disk even if you can't mount it.

---

