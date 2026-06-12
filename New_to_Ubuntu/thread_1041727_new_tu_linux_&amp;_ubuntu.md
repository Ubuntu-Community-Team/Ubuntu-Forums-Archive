---
title: "new tu linux &amp; ubuntu"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Zero31 on 2009-01-16
trying to install software on ubuntu
keep on getting the message (E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report)
What to do?

---

### Post by taurus on 2009-01-16
Close whichever window that you have opened when you got that error message.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Sealbhach on 2009-01-16
OK, this happens quite a bit and luckily the error message tells you what to do.

Open up a terminal, you'll find it in Applications/Accesories/Terminal and copy and paste this command:

```
sudo dpkg --configure -a
```

Enter your password when requested. That should fix it.


.

---

