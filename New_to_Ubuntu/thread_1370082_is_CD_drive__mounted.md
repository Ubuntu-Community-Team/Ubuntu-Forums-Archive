---
title: "is CD drive  mounted ?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by soryu on 2010-01-01
how can i check if my cd-r drive in mounted correctly?
shouldn't there be a CD drive icon in "places"?


there is a CDrom folder in my   /- file browser , but it's empty.

---

### Post by Max_Mackie on 2010-01-01
Try navigating to /media
I'm pretty sure that's where they get mounted.

You can also look under "Places" in the gnome menu.

---

### Post by soryu on 2010-01-01
there are 2 cdrom folder's in media both empty.
cdrom and cdrom0.
cdrom folder has an arrow on it??
no cdrom in gnome "places"

---

### Post by soryu on 2010-01-01
what does this mean?

linux@linux-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5a858d04-58a9-43df-b3a8-4c98a33fcc45 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b134a739-f335-4c3f-a918-4a0fc262e2a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
linux@linux-desktop:~$

---

### Post by Max_Mackie on 2010-01-01
From what I can see, your CD is not mounted.

Try doing this from the terminal:
```
mount /cdrom
```

Edit:
fstab says you have a CD mounted (scd0 on cdrom0).
I'm not quite sure what to do from here :S
I hope someone else can give you a hand. If not, try some Google-fu

---

### Post by soryu on 2010-01-01
linux@linux-desktop:~$ mount /cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

linux@linux-desktop:~$ 




:confused:

---

