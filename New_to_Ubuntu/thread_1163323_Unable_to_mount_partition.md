---
title: "Unable to mount partition"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by AncientPC on 2009-05-18
I have a jfs hdd in an external hdd that's always worked fine, but just the other day it was locked up and I couldn't unmount so I restarted the machine.  Now when I try to mount it I get:

```
root@punk:/media# mount /dev/sdd5/ blacx/ -t jfs
mount: wrong fs type, bad option, bad superblock on /dev/sdd5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg | tail returns:
```

[ 2507.344729] sdd1: rw=0, want=72, limit=2
[ 2507.344747] attempt to access beyond end of device
[ 2507.344752] sdd1: rw=0, want=128, limit=2
[ 2510.374396] attempt to access beyond end of device
[ 2510.374404] sdd1: rw=0, want=72, limit=2
[ 2510.374414] attempt to access beyond end of device
[ 2510.374420] sdd1: rw=0, want=128, limit=2
[ 2512.476773] attempt to access beyond end of device
[ 2512.476781] sdd1: rw=0, want=72, limit=2
[ 2512.476792] attempt to access beyond end of device
[ 2512.476797] sdd1: rw=0, want=128, limit=2
```

Any suggestions on how to save this partition?  It's my backup partition so I have lots of important information on there . . .

Edit: I manage to fix it by running fsck. I had mistakenly run `fsck /dev/sdd5/` earlier which fails while `fsck /dev/sdd5` works fine.

---

