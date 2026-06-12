---
title: "need help with a 2nd hdd problem"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by Daverobb on 2009-10-12
I tried to reformat my 2nd hdd (which worked I think) and then remount it but it didnt work and i believe i got the ID mixed up -- doesnt it look like I mounted my primary drive (/media/sda1) as /sdb1 also??  Confused and need help ...

```
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             37728456  27274508   8537396  77% /
tmpfs                   516756         0    516756   0% /lib/init/rw
varrun                  516756       208    516548   1% /var/run
varlock                 516756         0    516756   0% /var/lock
udev                    516756      2892    513864   1% /dev
tmpfs                   516756       380    516376   1% /dev/shm
lrm                     516756      2204    514552   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sdc1            488264768 331992352 156272416  68% /media/FAT32
/dev/sda1             37728456  27274508   8537396  77% /media/sdb1
```

---

### Post by unutbu on 2009-10-12
It is possible to mount the same partition at multiple mount points.

The output of df is showing that the partition /dev/sda1 is mounted at / and also at /media/sdb1. 

You can umount /dev/sda1 from /media/sdb1 by running the command
```

sudo umount /media/sdb1
```

This will leave /dev/sda1 mounted at /.

Then you can mount /dev/sdb1 at /media/sdb1 by running
```

sudo mount /dev/sdb1 /media/sdb1
```
I hope you did not reformat /dev/sda1 by mistake. I suppose you must not have, or else your machine would not be running right now... :)

---

