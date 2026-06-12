---
title: "problem in config file"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by ak331 on 2009-01-28
I tried to install a package and something happened and I have a message that package need to be installed but when I tried to install it it gives the message as follows

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when I tried to run the command it tells me that I need to be superuser

when I type su in terminal window and prompts me for password and get a message that authentication failed.

need help

---

### Post by gettinoriginal on 2009-01-28
```
sudo dpkg --configure -a
```

Also, cache open usually means that you have more than one package manager open at the same time.  When trying to install a program, you can only have **one** package manager open ie: synaptic, terminal, add/remove

---

### Post by ak331 on 2009-01-28
resolved

---

