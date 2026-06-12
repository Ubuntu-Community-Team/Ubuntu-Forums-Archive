---
title: "Strange file properties"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by haarvik on 2009-01-09
Ok, so I was doing an apt-get install and started getting input/output errors.  I did an ls -l on /usr/share/bug/ and one of the files has this for the properties:

ls: cannot access /usr/share/bug/xserver-xorg-video-intel: Input/output error
total 0
d????????? ? ? ? ?                ? xserver-xorg-video-intel

how do I fix that?

---

### Post by Joeb454 on 2009-01-09
That's very odd...

Here's what mine says, you may need to do some chown and chmod'ing ;)

```
joe@nero:~$ ls -l /usr/share/bug/ | grep xserver-xorg-video-intel
drwxr-xr-x 2 root root 4096 2008-10-29 23:02 xserver-xorg-video-intel

```

---

### Post by haarvik on 2009-01-09
Nope, no matter what I try I get input/output error.

---

### Post by haarvik on 2009-01-09
Gave up, fdisk'd and restarted.

---

