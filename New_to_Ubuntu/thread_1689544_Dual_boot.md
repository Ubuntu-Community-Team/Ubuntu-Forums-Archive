---
title: "Dual boot?"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2011-02-16
Let me start off by saying: I've been using ubuntu only for the past 2.5 years, and I love it.  My laptop died on me, so my mum got me a new one for my birthday.  It's a Dell Inspiron M5030.  I have Win7 and several apps I want to keep (Microsoft Office, until it can run 100% in WINE) so I would like to setup a dual boot system.  The problem is: I don't want to have a GRUB nightmare.  I've seen screenshots of people with like a million kernals listed.  Is it possible to have it set up to, no matter how many new kernels there are installed, I see only two options: Ubuntu 10.10 (or whatever version) and Windows 7?  Please detail the process.

---

### Post by cjv8888 on 2011-02-16
If you only like to see one kernel listed, just remove the older kernels either through synaptic or Ubuntu Tweak as soon as you are sure the newest one works.  I don't think there is any way of only seeing one kernel in Grub2 automatically.  You can physically put a # in front of the older kernel lines but once you run update-grub then it is back to the way it was.

---

### Post by wilee-nilee on 2011-02-17
Take a look at this link.
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

There is also Ubuntu tweak for removing kernels easily amongst other goodies.

---

