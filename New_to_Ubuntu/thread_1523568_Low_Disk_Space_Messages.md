---
title: "Low Disk Space Messages"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by bjbowen4 on 2010-07-03
Very new to ubuntu, hence the post in the beginner area.  Did some UNIX is school several years ago, but all I remember about that class is the cute chick that sat next to me. hahaha  One thing I am confused about.  Today I started getting low disk messages, such as "There are 0 kilobytes remaining on the disk..." I click examine to see what the issue is and the Disk Usage Analyzer is showing 216 GB available. I do a search for commands to investigate.  I use df -h and the result is:  

Filesystem            Size  Used Avail Use% Mounted on 
/dev/loop0             17G   16G     0 100% / 
none                  1.5G  288K  1.5G   1% /dev 
none                  1.5G  216K  1.5G   1% /dev/shm 
none                  1.5G   88K  1.5G   1% /var/run 
none                  1.5G     0  1.5G   0% /var/lock 
none                  1.5G     0  1.5G   0% /lib/init/rw 
/dev/sdb1             233G   18G  216G   8% /host  

so I imagine is talking about /dev/loop0.  Question is, what is that? and why is the whole darn thing taken up? and what do I do to solve the problem.

---

### Post by Ocxic on 2010-07-03
The real question is why "/dev/loop0" is your root partition. That is very weird.

---

### Post by bjbowen4 on 2010-07-03
You got me, I fired up wubi, selected some options and let it run.  Any ideas for a solution?

---

### Post by Ocxic on 2010-07-03
well low disk space ussually you have to delete/ uninstall some stuff.

try "sudo apt-get clean" that will remove cache package downloads. but might not be much.

I'm not familiar with wubi installs so that might explain why root is on /dev/loop0.

---

### Post by bjbowen4 on 2010-07-04
I think what I'm going to do is format the whole disk I have ubuntu installed on. (Want to change it all to ext4 anyway) then reinstall ubuntu through a bootable CD instead of wubi.  That way I can make more space for root in the process.

---

### Post by warfacegod on 2010-07-04
If you do take that route, you might consider have a few separate partitions.

A small one for root, the OS. 10 -15 GB should be ample room for growth.

A very big partition for /home

And possibly another for swap. Slightly larger than your RAM. Personally I don't use one.

---

### Post by bjbowen4 on 2010-07-04
Yup that's what I did had a 500gb hd that has windows on it, then a 250 that I'm using for Ubuntu.  Of course now windows won't boot properly..haha.  Keeps wanting to boot into recovery mode for whatever reason.  Nothing like a little push to get away from Windows.

---

