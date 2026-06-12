---
title: "CD to usb drive Ubuntu Server"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Ripfox on 2009-01-26
I need to install a deb file with no network connection. I need to cd to the thumb drive, says it is not in fstab when I do cd /dev/sdb or sdb1.

Also, side note...this is my first sever (hence absolute beginner) :)

Why does the info spill out when you type ls --help to the bottom?
How do I read it from the beginning of the help file?

Thnx!

---

### Post by gborzi on 2009-01-26
First problem: /dev/sdb is the device, not the directory where your thumb drive is mounted. On the desktop install, the directory is under /media/<something> where <something> is the volume label, if any, or simply disk.
Type *mount* on a shell and you should see an output like this > /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda9 on /home type ext3 (rw,relatime,user_xattr)
/dev/sda7 on /usr type ext3 (rw,relatime)
/dev/sda8 on /usr/local type ext3 (rw,relatime)
....
if you see a line beginning with /dev/sdb1 then the directory is after the *on* word. I don't know if it works in the same way on an server install. If this is not the case, let me know.
Second problem: type *ls --help|less*which means that the output of ls --help is given to the less command as input. Then you can scroll up/down the output with yours up/down arrows.

Hope this helps.

---

### Post by Ripfox on 2009-01-26
Thank you...that all worked.

:)

---

