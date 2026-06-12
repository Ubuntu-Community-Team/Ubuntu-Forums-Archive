---
title: "How to change my screen resolution from within the bash shell"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Spottydog on 2010-08-22
Is there anyway iI can alter the settings for my screen resolution BEFORE logging in to Ubuntu 10.04?  When I log in my screen fades away to white.  I'm using a dell inspiron 6000 and if I run ubuntu from a USB stick, it starts fine, if I change the resolution, I get the same fade to white screen that I am getting with my actual installed version on that laptop.

It's all because i upgraded from 9.04 to 10.04 that i've been having this problem.  

So, it seems to me that my settings on my installed version must be set for the wrong resolution.  If i can manage to work my way to the bash shell before actually logging on to my computer, can someone please tell me the code to enter ino order to change my screen resolution to 1920x1200 (16;10)??

If you can, I'd be MOST grateful :)

Thanks so much.

---

### Post by Matt__ on 2010-08-22
I believe you can do 

```
nano -w /etc/X11/xorg.conf
```

scroll down and change the res to one you want.

---

