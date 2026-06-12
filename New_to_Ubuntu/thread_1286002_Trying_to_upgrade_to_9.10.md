---
title: "Trying to upgrade to 9.10"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Xoanan on 2009-10-08
Hi All!

I am attempting to upgrade to 9.10 Karmic and for some reason, it keeps failing saying that only a partial upgrade is possible or the install becomes unstable and must close. I realize its beta, but is anyone else having this issue?:popcorn:

---

### Post by philinux on 2009-10-08
> **Xoanan said:**
> Hi All!

I am attempting to upgrade to 9.10 Karmic and for some reason, it keeps failing saying that only a partial upgrade is possible or the install becomes unstable and must close. I realize its beta, but is anyone else having this issue?:popcorn:

Please have a look here:-

[http://ubuntuforums.org/showthread.php?t=1280021](http://ubuntuforums.org/showthread.php?t=1280021)

[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

---

### Post by Xoanan on 2009-10-09
> **philinux said:**
> Please have a look here:-

[http://ubuntuforums.org/showthread.php?t=1280021](http://ubuntuforums.org/showthread.php?t=1280021)

[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)


Thanx!

I may have found something else; it appears that 9.10 uses ext4 filesystem and I am using ext3
```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

Someone in another thread I found mentioned that if you are on ext3, a clean install is best rather than an upgrade

---

### Post by ptn107 on 2009-10-09
Filesystem won't matter.

---

### Post by Xoanan on 2009-10-09
Looks like I was successful in the upgrade!

```
xoanan@ubuntu:~$ lsb_release -r
Release:	9.10
xoanan@ubuntu:~$ 

```

Now to explore....

---

### Post by philinux on 2009-10-09
> **Xoanan said:**
> Looks like I was successful in the upgrade!

```
xoanan@ubuntu:~$ lsb_release -r
Release:	9.10
xoanan@ubuntu:~$ 

```

Now to explore....

See the new sticky on the karmic forum. Very good advice there.

---

