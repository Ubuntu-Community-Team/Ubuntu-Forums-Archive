---
title: "cdrom permissions dissapear"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by crabclaw on 2009-04-29
Trying to burn ubuntu iso for a friend in 9.04. If I run 

```
sudo gedit /etc/fstab 
```

I get this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=637a7b8f-2352-4786-b223-40e2c906a850 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=40f5ff7d-9676-4a03-a0ad-1bc0ec9ad6b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


What should I change it to?

---

### Post by taurus on 2009-04-29
You don't have to change anything in /etc/fstab.  Just insert a blank CD and use one of those cd/dvd burners to burn the ISO image to a disc then.

---

### Post by crabclaw on 2009-04-29
the problem is that any of the programs I use just don't work. They all stop at 4% and I'm left with a coaster! The cd's are good, it's just the cd won't be written to.

---

### Post by taurus on 2009-04-29
What app do you use to burn the ISO image to a CD?

What's the output of this command from a terminal?

```
id
```

---

### Post by crabclaw on 2009-04-29
I'm using Brasero

Here's the output:

```
 id
uid=1000(jonathan) gid=1000(jonathan) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(jonathan)

```

Thanks

---

### Post by taurus on 2009-04-29
Try another app like k3b.

---

### Post by crabclaw on 2009-04-29
It didn't work last time and there was an update released in the meanwhile so I uninstalled/purged & reinstalled both brasero and k3b and it still doesn't work. I do on the other hand have a growing collection of coasters. You want one?

What shall I try now?

---

### Post by sneeks on 2009-04-29
i have this same problem in xubuntu 9.04,once installed the system will not open the optical drive's .
say read only no permissions...
i will wait for an update me thinks.

---

