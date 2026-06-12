---
title: "Can't log in as Edubuntu client"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by hsweet on 2007-04-24
I (whoops) hit the power button at an inopportune time and now the client computers cannot get to the edubuntu login screen on Edgy (6.10).  DHCP is fine but the clients end up in Busybox.

Further, I get this message when the machine boots.  sda2 is the extended partition with the swap file.

```
e2fsck 1.39 (29-May-2006)
e2fsck: No such file or directory while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

fsck does not want to fix it :( 

PartII   .. I installed Feisty Edubuntu on same machine, different drive.  I can log in (the first user) on a client, but nobody else can.  Goes back to login screen even though the log file says the password is accepted.

I'll use any system that works..

---

