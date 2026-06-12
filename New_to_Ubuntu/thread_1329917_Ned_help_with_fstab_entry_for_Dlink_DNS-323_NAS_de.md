---
title: "Ned help with fstab entry for Dlink DNS-323 NAS device"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by tele_mark on 2009-11-17
I tried to post this in [this thread]("http://ubuntuforums.org/showthread.php?t=532996"), but the system isn't letting me, so I have to start one here. 

Like the OP of that thread, I'm trying to make an fstab entry for my Dlink dns-323 NAS box,so I can access it easily from applications that don't know about .gvfs . Unfortunately, I'm not having good luck like he did. 

This is the entry I made in fstab:

```
//DLINK-09AFB0/Volume_1     /mnt/dlinkNAS    smbfs    user,rw,sync,noauto,exec,uid=mark  0    0
```And this is the error I'm seeing when I try to mount the share:

> mark@Dell1501:/etc$ mount /mnt/dlinkNAS
mount: wrong fs type, bad option, bad superblock on //DLINK-09AFB0/Volume_1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
I've tried it with the ip address of the device instead of the name, and get the same result.
Can anyone steer me in the right direction?

---

