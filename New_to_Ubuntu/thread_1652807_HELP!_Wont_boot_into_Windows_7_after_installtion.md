---
title: "HELP! Wont boot into Windows 7 after installtion"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by laugh1 on 2010-12-25
I installed everying and it went fine. I chose to install it ALONGSIDE OTHER OPERATING SYSTEMS and gave it 5 gigabytes BUT WINDOWS 7 IS GONE!!!

Help me please, I check the bios and boot options but nothing is there and it boots into ubuntu only.

help me!!!

---

### Post by TeoBigusGeekus on 2010-12-25
Applications>Accessories>Terminal
Post us the output of 
```
sudo fdisk -l
```
That's L, not 1.

---

### Post by laugh1 on 2010-12-25
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e45c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37384   300281856   83  Linux
/dev/sda2           37384       38914    12286977    5  Extended
/dev/sda5           37384       38914    12286976   82  Linux swap / Solaris

```

Looks like it's gone.....

---

### Post by TeoBigusGeekus on 2010-12-25
What's sda2?
Post us the output of
```
df -h
```
as well.

---

### Post by laugh1 on 2010-12-25
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             282G  2.1G  266G   1% /
none                  1.8G  240K  1.8G   1% /dev
none                  1.8G  324K  1.8G   1% /dev/shm
none                  1.8G  124K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  282G  2.1G  266G   1% /var/lib/ureadahead/debugfs

---

### Post by TeoBigusGeekus on 2010-12-25
You have my condolences...
Anything important in the windows partition?

---

### Post by laugh1 on 2010-12-25
damnit i had quite a bit. how could this happen?!?!?! i followed everything exactly!

i have a recovery disc...

---

### Post by Quackers on 2010-12-25
Is this version 10.10 by any chance?
The "install alongside" option has been known to do this.

---

