---
title: "Partitioning Errors."
date: 2009-05-19
forum: New to Ubuntu
---

### Post by nava2 on 2009-05-19
Okay, here is the story.

I installed Ubu, found I had no space. Reinstalled, ended up createing a whole new OS installation, ONTOP of the old. I cleared the old out out, and now I cannot boot.

I get the Grub Loading Error 22. 

I believe I need to remount the new partitions but I have no idea how.

Any help is appreciated.

---

### Post by qjmoss on 2009-05-19
This happened to me,


For about two weeks i looked for a fix.. nothin.

After awhile. 

I came across

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


Read up on this. and i'm sure this could fix your error

---

### Post by mapes12 on 2009-05-19
> I believe I need to remount the new partitions but I have no idea how.
 If Grub is working correctly you will not have to mount your main operating partitions. It will be done by default. I'm assuming you are just looking to install Ubu and have no other OS. That being the case then you can reconfigure your partitions using a GParted LiveCD and start again. Alternatively, wipe your HDD using something like DBAN and start again. See the link below in my signature file for more installation solutions if you have other OS's on your machine.

---

