---
title: "dpkg interrupted"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by The Linux Nub on 2009-08-01
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.


How in the world do I fix this upon opening up Synaptic Package Manager?
I am wanting to clean off my system (for lack of better words) and I get that message upon opening up that application. Help would be appreciated :) also FYI, im sorta new to linux based OS's so pretty much as much as help as possible (cant install updates - says i need more room on '/'...)

---

### Post by Sef on 2009-08-01
Applications > Accessories > Terminal

Then copy and paste this command in the Terminal:

```
sudo dpkg --configure -a
```

After running that command, your system should work fine.

---

### Post by The Linux Nub on 2009-08-01
Thank you so much, it worked! =]

---

### Post by Sef on 2009-08-01
> Thank you so much, it worked! =]


You're welcome.  Please post any problems and questions with Ubuntu in these forums.

---

