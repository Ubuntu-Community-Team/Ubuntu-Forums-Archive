---
title: "update error"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by dzon65 on 2009-09-16
I tried to install some updates but got this error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
I put it in a terminal but got the following (trying to translate):...this can only be done by owner.Would appreciate some help with this cause I can't access synaptics due to this.
Thanks in advance.

---

### Post by halitech on 2009-09-16
when you run dpkg --configure -a in the terminal, run it as sudo
```
sudo dpkg --configure -a
```

---

### Post by dzon65 on 2009-09-16
Thank you.Still have a LOT to learn.So,if I get it wright,sudo is something like taking ownership,superuser?By the way,the update was about MS fonts,already installed windows fonts,hope they don't interfere.Anyway,thanks a lot

---

### Post by halitech on 2009-09-16
yes, sudo gives you temporary admin rights to run a command. Most users will install the MS Core fonts so websites look closer to the way they were designed and shouldn't cause any problems.

---

