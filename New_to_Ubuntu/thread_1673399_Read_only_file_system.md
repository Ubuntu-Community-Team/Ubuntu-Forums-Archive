---
title: "Read only file system"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by blumaa on 2011-01-22
Hello,

I booted up ubuntu today and found that the files on my external hard drive AND my internal hard drive are read only.  I cannot change their permissions with any chown or remount command even when I switch to root user.  Does anyone have any idea what the problem is?  Help!

I am running ubuntu 11.04, Natty Narwhal.

Thanks.

---

### Post by kevdog on 2011-01-22
This probably has to do with the way the volumes were mounted with the mount process.  Do a search for the remount command on the forums since I'm no expert on it myself.

---

### Post by blumaa on 2011-01-22
Thanks.  I have no idea how or why I would need to remount the filesystem.  Any suggestions on how to do that, anyone?

---

### Post by [Snc] on 2011-01-22
> **blumaa said:**
> Hello,

I booted up ubuntu today and found that the files on my external hard drive AND my internal hard drive are read only.  I cannot change their permissions with any chown or remount command even when I switch to root user.  Does anyone have any idea what the problem is?  Help!

I am running ubuntu 11.04, Natty Narwhal.

Thanks.

Are all file systems supporting Linux permissions?

about remounting: [http://www.linuxquestions.org/questions/linux-newbie-8/remount-using-fstab-entries-269127/](http://www.linuxquestions.org/questions/linux-newbie-8/remount-using-fstab-entries-269127/)

---

### Post by matt_symes on 2011-01-22
Hi

> I am running ubuntu 11.04, Natty Narwhal.

This is your test system ?

You could try fsck from a liveCD if it's a linux filesystem. That might fix it.

Kind regards

---

