---
title: "&quot;Read-only file system&quot; on disk without hardware errors"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by ronbarak on 2010-07-29
Hi,

I have Ubuntu 10.04 installed as WUBI on Windows 7 on a laptop.
I have an external NTFS disk connected via USB (/dev/sdc1).
I had to reboot the machine while there were still programs accessing [COLOR="Navy"]/media/931 GB[/COLOR] and since then every action that wants to write to this filesystem fails:

```
$ touch /media/931\ GB/tmp.tmp
touch: cannot touch `/media/931 GB/tmp.tmp': Read-only file system
``` 

however, the disk is supposed to be mounted rw:

```
$ mount | grep sdc1
/dev/sdc1 on /media/931 GB type ntfs ([COLOR="Red"]rw[/COLOR],nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077)
```

I restarted the laptop into the Windows 7, to see how the disk looked from Windows' point of view. 
While there, I also checked (and fixed) for errors.
In any case, now the disk is okay on the Windows 7, and writes are possible there.
So, hardware errors don't seem to be the culprits.

I Restarted the laptop again to Ubuntu.

Still, no write operations are possible on /dev/sdc1.

I googled, but seems others that had the same problem solved them by fixing hardware errors, which does not seem to be my case.

I tried to remount, to no avail:

```
$ sudo mount /dev/sdc1 /media/931\ GB/ -t ntfs -o rw,remount
$ touch /media/931\ GB/tmp.tmp
touch: cannot touch `/media/931 GB/tmp.tmp': Read-only file system
```

Can you suggest what can I do ?

---

### Post by ronbarak on 2010-07-29
After some more research, I found that the package that gives NTFS write capability is *ntfs-3g*.
I reinstalled it, and then used it to make the NTFS filesystem rw.
[COLOR="Blue"]Voilà, it worked.[/COLOR]

---

