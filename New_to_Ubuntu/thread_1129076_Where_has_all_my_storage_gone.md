---
title: "Where has all my storage gone?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by thenickdude on 2009-04-18
Hey everyone,

I'm running a little Ubuntu server (on Amazon's EC2) for my sister's website and we're running out of storage space on our root partition. Thing is, I can't work out where it is all going. Here's uname -a:

```
Linux domU-12-31-38-01-68-A1 2.6.21.7-2.fc8xen #1 SMP Fri Feb 15 12:34:28 EST 2008 x86_64 GNU/Linux
```

The output of df:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             10403128   8907860    970980  91% /
varrun                 3936020        72   3935948   1% /var/run
varlock                3936020         0   3936020   0% /var/lock
udev                   3936020        24   3935996   1% /dev
devshm                 3936020         0   3936020   0% /dev/shm
/dev/sdb             433455904    488008 410949592   1% /mnt
/dev/sdh              10403128   7702136   2176704  78% /vol
```

And the output of mount:

```
/dev/sda1 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdb on /mnt type ext3 (rw)
/dev/sdh on /vol type ext3 (rw)
```

So, what I think that tells me is that my root partition (from device /dev/sda1) is 10GB large and is 91% full. It keeps filling up entirely and I have to trim webserver logs, application caches, etc to make room. Otherwise, MySQL has no place to store temporary files and queries start failing for lack of disk space (the database itself is on /vol).

But where are all the files that are filling up my root partition? If use this command:

```
cd /
sudo du -hs *
```

I get this output:

```
4.7M    bin
112K    boot
24K     dev
8.7M    etc
12K     home
4.0K    initrd
66M     lib
3.7M    lib32
0       lib64
16K     lost+found
329M    mnt
4.0K    opt
0       proc
96K     root
6.5M    sbin
4.0K    srv
0       sys
12K     tmp
595M    usr
251M    var
7.2G    vol
```

Apart from "vol", the other files equate to less than 1.5GB, and this is what I expect the usage on /dev/sda1 to be. But it looks like "vol" is contributing to the space taken up on /dev/sda1. How can this be? /vol is a separate device, it's a 10GB detachable drive. What am I misunderstanding here? Why is my root partition filling up, stopping me from writing any more to it?

---

### Post by blueridgedog on 2009-04-18
I use something similar to your du:
cd /
sudo du --max-depth=1 | sort -g

Also, you may have a trash files around:

You can:

sudo rm ~/.local/share/Trash/files/*

(I recommend you look at them first)

---

### Post by thenickdude on 2009-04-19
Rebooting the sever cured it and I figured out why. Our weekly Apache access logs were 6GB each. I deleted them the other day, but they were open at the time - Apache was holding them open. They disappeared from the file system, but were still stored on the disk until Apache closed them. Now my root partition is only 11% full.

---

### Post by blueridgedog on 2009-04-19
Odd that they did not show up in your du command.

---

### Post by thenickdude on 2009-04-20
They didn't show up because they were no longer a visible part of the filesystem. The only program that could see them would be the one that had them open when they were deleted.

---

