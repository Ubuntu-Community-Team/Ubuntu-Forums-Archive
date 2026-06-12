---
title: "Target filesystem doesn't have requested  /sbin/init."
date: 2011-03-13
forum: New to Ubuntu
---

### Post by nu_buntu on 2011-03-13
hi, I am new to linux.

just a couple of days back, I had Ubuntu 10.10 installed on a new (and empty : for linux only) HDD. which worked superb untill...

due to power failure my machine got turned off, only to show following msg when i switched it on:

[B]Target filesystem doesn't have requested  /sbin/init.
No init found. Try passing init=bootarg.[/B]

please help. thanx.

---

### Post by llamabr on 2011-03-13
I assume you get a prompt?

try fsck'ing your disk:

```
fsck /dev/sda3
```
 or sda2 or whatever.  If you do not get a prompt, you can do the same with a livecd.

---

### Post by nu_buntu on 2011-03-13
Thanks! for ur quick reply.

This is what I got when I tried while booting from HDD.

```
fsck /dev/sda1
/bin/sh: fsck: not found
(initramfs) _
```

Then I tried booting from my USB drive and used the terminal, which showed following:

```
ubuntu@ubuntu:~$ fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root
```

so, T tried using sudo:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$
```

and one more thing... when I try to open same HDD by double clicking it shows:

```
Unable to mount location
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed:
An operation is already pending
```

I dont mind re-installing OS, but before that, I just want to get my data back.

---

