---
title: "system choked"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by 007casper on 2011-05-27
on the hard drive manager I picked the recommended nvidia driver
on the restart the system choked.

It says 
Gave up waiting for root device.  Common problems
Boot args (cat /proc/cmdline)
check rootdelay=(did the system wait long enough?)
check root=(did the system wait for the right device?)
Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/2f67c21a-5f8b-41c0-82c90-670a9b3f7377 does not exist.  Dropping to shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

you can even type on the shell

???

---

### Post by 007casper on 2011-05-27
nobody has an idea what this is about.  I even reinstalled the system, and then had the same problem.  

please advise.  Thank you.

---

### Post by 007casper on 2011-05-28
I think boot partition got corrupted when I was updating drivers.  Reformatted the hard drive all seems ok

---

