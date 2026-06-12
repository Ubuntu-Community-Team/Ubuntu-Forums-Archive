---
title: "Question on 'mounts' - (unplugging drives etc)"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-01
Hi

I assume that it is never safe to unplug a flash portable drive from my laptop just by pulling it out...is this what is meant by 'unmounting?

What is the safest way to remove hardware from your machine?

Thanks!

---

### Post by ajgreeny on 2009-02-01
> I assume that it is never safe to unplug a flash portable drive from my laptop just by pulling it out...is this what is meant by 'unmounting?

What is the safest way to remove hardware from your machine?
To 1, the answer is an unqualified "Yes" and that is exactly what is meant by unmounting.
To 2, I suggest you use the panel applet Disk mounter which lets you do the mounting and unmounting of all disks, internal and external with two clicks.  Very quick and very, very useful.

---

### Post by krzysz00 on 2009-02-01
Right-click on the icon on the desktop and pick "Unmount Volume" or "Eject Volume". This is basically the Ubuntu version of safely remove hardware. 
As for "mounting" and "unmounting" and why they're called that, it works like this
[LIST]
[*]In Ubuntu and every other Linux, everything start from / a.k.a. root
[*]"Mounting involves taking the files and directories on a different partition and/or disk and referring (nothing is actually copied) to a directory under root (like /media/disk)
[*]Unmonting removes that reference, making it possible to remove the drive because no one (even the Linux kernel) is accessing the files on the drive
[*]At the command line the mount and umount commands let you have a lot of control over mounting.
[/LIST]
This info may not be 100% correct, and feel free to correct me but this is what I know in my attempt at not being technical

---

### Post by listerdl on 2009-02-02
Thanks for the replies, just wanted to be sure! Thanks, Lister

---

