---
title: "Where is the Ubuntu Linux kernel located?"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-11-16
I am curious because I wanted to play around with Kernel Check, but I ran out of room. I was in the middle of compiling a kernel and completely ran out of space on my /. How can I get rid of kernel that failed?

Also, how much room is required to compile the kernel?

---

### Post by dca on 2009-11-16
Out of habit, I put the source in /usr/src/*
 
The running one is loaded from /boot/vmlinuz*

---

### Post by slughappy1 on 2009-11-16
What is usually in /usr/src? Mine currently has several folders totaling about five gigs. What is safe to remove in there?

---

### Post by dca on 2009-11-16
They should all be labeled, mine currently holds only two directories: the actual kernel source directory and the kernel headers for my running kernel...

---

### Post by slughappy1 on 2009-11-17
So my /usr/src looks like ```
total 24
drwxrwsr-x  6 root src  4096 2009-11-16 19:55 .
drwxr-xr-x 11 root root 4096 2009-11-16 05:40 ..
lrwxrwxrwx  1 root src    21 2009-11-16 05:56 linux -> /usr/src/linux-2.6.31
drwxr-xr-x 25 root root 4096 2009-11-16 19:08 linux-2.6.31
drwxr-xr-x 23 root root 4096 2009-10-27 18:16 linux-headers-2.6.31-14
drwxr-xr-x  7 root root 4096 2009-10-27 18:16 linux-headers-2.6.31-14-generic
drwxr-sr-x  2 root src  4096 2009-11-16 05:37 oldpackages

```
I should be able to remove the following correct?
linux
linux-2.6.31
linux-headers-2.6.31-14
oldpackages

---

### Post by zeroseven0183 on 2009-11-17
I'm just wondering why this stuff is in the Absolute Beginner Talk section?

Makes my nose bleed.

---

### Post by slughappy1 on 2009-11-17
Was there a better place to put it? I didn't notice a kernel section ;-)

So I was being a little slow yesterday. I should have just looked at the time stamps in /usr/src. I did indeed delete the files and folder that I listed above and nothing went wrong.

Also, I find it a little weird that when there is no space left in the / partition. That Gnome says the Power Manager isn't setup properly and to contact the Admin.

---

