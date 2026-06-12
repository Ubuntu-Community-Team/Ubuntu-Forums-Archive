---
title: "Boot up problem"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by ericstrom on 2010-06-26
Running Lucid Lynx 10.04

I let the PC keep running for a few hours while I went out. When I got back I had a black screen and the PC was locked up. So I did a hard reboot; shutting it down and turning it back on. When I booted back up I had a black screen with initramfs prompt waiting for input. Other messages above that are as follows :

mount: mounting/dev on /root/ dev failed: No such file or directory
mount: mounting/ sys on/root/sys failed: No such file or directory
mount: mounting/ proc on/root/proc failed : No such file or directory

Target file system doesnt have /sbin/init
No init found
Try passing init = bootarg
BusyBox v1.13.3 (ubuntu 1:1.1.13 ubuntu11)
initramfs _

This is the second time I've had this problem in the last few weeks. I was running jaunty and had it. So I tried clearing it off and starting with 10.04. It worked fine for a few days but now seeing the problem again.

What caused this and what do I do to get running again ?

---

### Post by arrange on 2010-06-26
First I would boot into a LiveCD, launch GParted and check the partition for errors (*Partition &#8594; Check*).

---

### Post by jmszr on 2010-06-26
ericstrom,

Do you happen to be using a Wubi install?

---

### Post by ericstrom on 2010-06-26
JMSZR

I am not using Wubi. Any other suggestions ?

---

### Post by -kg- on 2010-06-26
I've seen this problem several times before in the forums.  I'm more than half-way convinced that it's a hard drive about to go out (if it hasn't already).

Have you tried arrange's suggestion?  For some reason, you are unable to:

> [COLOR="Red"]mount:[/COLOR] mounting/dev on /root/ dev failed: [COLOR="Red"]No such file or directory[/COLOR]
[COLOR="Red"]mount:[/COLOR] mounting/ sys on/root/sys failed: [COLOR="Red"]No such file or directory[/COLOR]
[COLOR="Red"]mount:[/COLOR] mounting/ proc on/root/proc failed : [COLOR="Red"]No such file or directory[/COLOR]

Usually, when the system is trying to mount something and it fails with "[COLOR="Red"]No such file or directory[/COLOR]", that indicates that it can't find that "file" or "directory" where it expects to find it.  Since this is during the boot-up process, and since it has so many mount errors, I would say it's the "directories" that it can't "find."

Of course, a partition is a form of directory.  When you do a default install, the "/home" directory is created as a subdirectory to / (root), which is also considered a directory.  When you create a separate /home partition, it is mounted as a directory, even though it is on a separate partition.

Since you're having so many problems with mounting indicated at boot time, I would first suspect the hard drive.  It might be something else (like weak or failing RAM), but I would think that the ability to boot successfully to the Live CD would negate that.

It shouldn't be the installation, I don't think.  I run all my computers nearly 24/7, running BOINC work units and have never had any such trouble and a freeze and subsequent hard shutdown and reboot shouldn't have broken anything to that extent.  Add to that that you were having the same problem previously, and it points to hardware malfunction.

---

