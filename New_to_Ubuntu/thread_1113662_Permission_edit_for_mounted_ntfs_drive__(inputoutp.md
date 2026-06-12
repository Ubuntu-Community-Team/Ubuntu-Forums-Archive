---
title: "Permission edit for mounted ntfs drive  (input/output error)"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by gonzalo_gu on 2009-04-01
Hi there, i've just installed my Ubuntu F.F. and mounted the ntfs partition where i used to have all my Windows data. The thing is that i cannot modify anything in there, the drive is read-only. How do I change permission? For instance, i need to cp a file in order to install my modem and all I get is Input/output error. Since I'm not able to log-in as root in the graphic interface, how could I change permissions for that drive?
 I thank-u in advance.

---

### Post by llamabr on 2009-04-01
Hi.  Post the output of

```
cat /etc/fstab
```

---

### Post by gonzalo_gu on 2009-04-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc          	  /proc        	   proc    d	efaults        0       0
# /dev/sda1
UUID=f40d6f75-9e61-4dd5-bbc0-9cfb3e49bcea /              ext3    defaults,error
s=remount-ro 0       1
# /dev/sda5
UUID=21f4bf70-37d7-40b4-9a0c-f4be59849aae none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Mark Phelps on 2009-04-01
> **gonzalo_gu said:**
> Since I'm not able to log-in as root in the graphic interface, how could I change permissions for that drive?
 I thank-u in advance.

What, you can't do "sudo -i" in a terminal?  That will grant you root permissions for the remainder of that terminal session.

---

### Post by egalvan on 2009-04-01
> **gonzalo_gu said:**
> . Since I'm not able to log-in as root in the graphic interface, how could I change permissions for that drive?
 I thank-u in advance.

gksudo is used for running graphical apps in a gui environment.

for example...
```
gksudo nautilus
```

---

