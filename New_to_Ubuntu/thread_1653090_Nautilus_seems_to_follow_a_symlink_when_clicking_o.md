---
title: "Nautilus seems to follow a symlink when clicking on /usr/bin"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by jose_maria0 on 2010-12-26
Hi, all
I was trying to make a live-usb using live_helper. I created a folder named ~/live and executed live_helper from there.
After that, when I try to enter /usr/bin from Nautilus, it jumps to ~/live instead.
I can access /usr/bin from the console without problems and list the contents.
I have copied /usr/bin to ~/usr/bin in order to experiment with different solutions. ~/usr/bin shows the same behaviour as /usr/bin.
I have renamed ~/live to ~/live-bak and clicked (in Nautilus) ~/usr/bin and I got an error message: (something as) > "Cannot find /home/jose/live", check spelling and try again"
In syslog I find and entry:
```
kernel: [ 8147.583183] nautilus[12249]: segfault at bee84fac ip 00d3bccc sp bee84fb0 error 6 in libgobject-2.0.so.0.2600.0[d0d000+40000]
```
I have changed the folder permissions to ~/usr/bin ticking off the execution flag and affecting the contained files and sufolders. Then I can access the folder without problems. So I suspect there is an auto-executing script or something in ~/usr/bin which is causing Nautilus to try to open ~/live instead.
Any hint about how to find the "evil" script to send it to "hell":)

Thanks
Jose

---

### Post by jose_maria0 on 2010-12-27
I have found the cause of the problem. It is a symlink circular reference, which causes the Nautilus instance to close.
I had a second Nautilus instance showing the ~/live directory, when the other Nautilus window disappeared, then this became visible and produced the same effect as if it was a jump to ~/live from /usr/bin :o
After some work I found that the circular reference was between two symlinks: orte-checkpoint <--> ompi-checkpoint, pointing to each other. I found also a second circular reference between: orte-restart <--> ompi-restart.

I removed both circular references and the problem disappear:D

---

### Post by XeonBloomfield on 2010-12-27
Welcome **jose_maria0**

So if problem is solved mark thread as SOLVED. You can do it by clicking "Thread Tools" near first post upper-right corner and selecting "Mark thread as SOLVED". 

Regards, Xeon.

---

