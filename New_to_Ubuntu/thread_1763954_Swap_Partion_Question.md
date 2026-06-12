---
title: "Swap Partion Question"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by Mccfuzz on 2011-05-21
Hi
Eventually installed Ubuntu sandwiched between two win2k installations.
Prior to installation I prepared another partion of 2gb (too large maybe) as the swap partion.
During installation via the advanced route I kept being confronted with 'no root file'.
I overcame this problem ( not really knowing what I was doing) by adding a '/' somwhere.
It then proceeded to install.
There was never any mention of the swap partion.
How can I be certain that my designated partion is being utilized or that I even have a functioning swap partition?
Thnx all!!

---

### Post by jerome1232 on 2011-05-21
What are the contents of your fstab?

```
cat /etc/fstab
```

---

### Post by lmarmisa on 2011-05-21
You can see the partition, partitions or even files which are being used for swap typing this command:

```

sudo swapon -s

```

---

### Post by Mccfuzz on 2011-05-21
Hi

Requested info:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=27bd24cf-a4d8-48a4-9e31-73289296daa4 /               ext3    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
kevles@kevles-desktop:~$

---

### Post by jerome1232 on 2011-05-21
> **Mccfuzz said:**
> Hi

/dev/sda7       none            swap    sw              0       0


Looks like you definitly have sda7 set as your swap. I'm sure the swapon command given by lmarmisa would give you more detailed info.

---

### Post by grahammechanical on 2011-05-21
Another way of looking at this is through Disc Utility. You get a graphical representation of the hard disc. You will see which partition is labeled swap and how large it is.

Regards.

---

### Post by philinux on 2011-05-21
> **Mccfuzz said:**
> Hi
Eventually installed Ubuntu sandwiched between two win2k installations.
Prior to installation I prepared another partion of 2gb (too large maybe) as the swap partion.
During installation via the advanced route I kept being confronted with 'no root file'.
I overcame this problem ( not really knowing what I was doing) by adding a '/' somwhere.
It then proceeded to install.
There was never any mention of the swap partion.
How can I be certain that my designated partion is being utilized or that I even have a functioning swap partition?
Thnx all!!

Also for info. System>admin>system monitor. Resources tab.

---

