---
title: "Is it OK to update persistent USB install?"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-01-05
Hi!  I have Ubuntu 8.10 installed on one of my 4 GB flash drives.  I use it to boot Ubuntu on the school computers. ;)

I hesitate to install any updates, but I don't want to go without security vulnerabilities either.  Will it ruin my USB persistent install if I:

sudo apt-get upgrade

?

Thanks!

---

### Post by adult swim on 2009-01-05
it shouldnt be  a problem at all to update as long as there is room for the updates to be downloaded.

---

### Post by pi.boy.travis on 2009-01-06
Everything was upgraded perfectly, except for the kernel.  I would guess that this is because of some limitation of the live CD system.  However, I don't need the latest kernel, as the one that runs the live CD has everything I need.  Thanks!

Now I never have to use Windows again!

I hope. . .

---

### Post by pi.boy.travis on 2009-01-10
OK, a later update has broken Firefox and Open Office.

This is a know issue, and a bug report has been filed:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292159)

---

### Post by C.S.Cameron on 2009-01-10
If you are using a typical persistent install where persistence is saved in a file named casper-rw you will find that it gets filled up quickly and is not easy to clean.
Once filled your persistence is dead.
Better to make separate persistence partitions, casper-rw and home-rw, these are easy to clean or replace. 
However you still will not be able to update the kernel, for that you need to do a full install just like you would to internal HDD.

---

### Post by pi.boy.travis on 2009-01-10
> **C.S.Cameron said:**
> If you are using a typical persistent install where persistence is saved in a file named casper-rw you will find that it gets filled up quickly and is not easy to clean.
Once filled your persistence is dead.
Better to make separate persistence partitions, casper-rw and home-rw, these are easy to clean or replace. 
However you still will not be able to update the kernel, for that you need to do a full install just like you would to internal HDD.

Thanks for the tip!  I'll have to try that, but for now, I am going to disable updates altogether.

---

### Post by pi.boy.travis on 2009-01-11
The workaround on the bug page *does not* fix the problem.  The updates are installed correctly but apt-get still breaks.

---

