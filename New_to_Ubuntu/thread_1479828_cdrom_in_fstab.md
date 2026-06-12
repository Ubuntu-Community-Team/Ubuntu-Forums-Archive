---
title: "cdrom in fstab?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by mesmith on 2010-05-11
Did a clean install of 10.04 (xubuntu).  All is well.  I noticed that there are no entries in fstab for my cdrw and cdrw/dvd devices.  They seem to work okay.  Are entries not required?

---

### Post by Drenriza on 2010-05-11
Can you do an

```
cat /etc/fstab
``` 

and post the output?

My fstab looks like this in 10.04

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5a105be2-3f1a-4d9d-9086-94c9d7731030 /               reiserfs notail          0       1
# swap was on /dev/sda5 during installation
UUID=02582eef-092f-4a04-8571-c5a77623991e none            swap    sw              0       0
**_/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0_**
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       
```

bold and under-scored is my cdrom drive.

---

### Post by John Bean on 2010-05-11
> **Drenriza said:**
> My fstab looks like this in 10.04

Was that from a clean install? My (clean) Lucid installation has no CD/DVD entry in fstab, unlike my Jaunty installation which has. Both work perfectly so I didn't worry about it.

---

### Post by Drenriza on 2010-05-11
I upgraded from 9.10

---

### Post by John Bean on 2010-05-11
> **Drenriza said:**
> I upgraded from 9.10

Looks like that's the reason for the difference then. I have no idea how or why a clean Lucid install doesn't use a CD entry in fstab but it appears that it's supposed to be that way.

---

### Post by Drenriza on 2010-05-11
It sounds strange.

Since the whole point of the fstab. Is to define what drives needs to be booted at system-start-up.

What output does the ```
mount
``` give?

EDIT.
Are you sure that your cdrom drive arnt defined with an UUID. Universally Unique Identifier? instead of an device name.

---

### Post by John Bean on 2010-05-11
> **Drenriza said:**
> Are you sure that your cdrom drive arnt defined with an UUID. Universally Unique Identifier? instead of an device name.

It's not defined at all in fstab, nor is there the usual predefined mount point in /media. When a disk is inserted it seems that it gets mounted by fuse.

As I said it all works without any problem so I didn't worry about it; if I come across any need to force a fixed mount point I'll add one in fstab, but for now I'll leave it alone.

---

### Post by mesmith on 2010-05-11
Absolutely no cd entries in my fstab, but they work so I'll leave well enough alone.

Thanks, all.

---

