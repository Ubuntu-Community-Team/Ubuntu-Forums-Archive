---
title: "Weird CD / DVD problem"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-10-03
Hi there,

I'm busy burning some DVD's and encounter various weird errors. Sometimes if I insert a DVD or CD I can't even mount it, it said I don't have permission etc. I however CAN mount it with a terminal using sudo etc. Now the last couple of times I've tried to burn something (a data DVD), Brasero tells me: 

error while burning 
an unknown error occurred

I've got two DVD burners, it happens to both of them, I've been messing around with my fstab so I might have screwed up something accidentally =D So here it is:

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d42162c7-3f76-40ea-9996-e9a345cea1e7 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=554ffc32-bf5e-4ca6-85db-bb323a79df99 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by dvdhaar on 2009-10-04
Anyone? :)

---

