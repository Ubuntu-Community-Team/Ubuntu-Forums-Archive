---
title: "Trying to mount cdrom and dvdrom drives"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by cnaqe1 on 2008-12-19
hello, can anyone help me fix this problem. i'm trying to mount and change permissions for my cdrom and dvdrom drives, i can't  watch movies or listen to music without fixing this problem thanks you.

---

### Post by zvacet on 2008-12-19
```
sudo cp /etc/fstab /etc/fstab.bak
```

```
gksudo gedit /etc/fstab
```

and check if you have this line 

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

if you don´t add it to your fstab.Save file and close it.After restart you should be able to automaticly mount your cd/dvd drives.

---

### Post by GMachine_24 on 2008-12-19
Perhaps you can post the contents of your /etc/fstab file here for us to see:



```


cat /etc/fstab


```

Under Places>Computer are your CD and DVD players listed?



More information is always better. :)

---

### Post by trypanon on 2009-06-11
hi all,
i just have identical issue. here comes the content of my fstab:

[PHP]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1c1e3706-9c56-4cae-b083-93049ee14068 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=4f433eed-4364-414b-9d86-061ebf89966d /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=ad153ca7-da00-44ef-9507-1f4f28671f57 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/PHP]

wtf is happening?

---

### Post by Gemu on 2009-07-12
Mine is doing the same thing. Every time I load an audio cd into the drive all of its contents are locked and I dont seem to be able to cd into the drive at all. I can't copy it out, cant burn a cd. This is extremely frusterating.

---

