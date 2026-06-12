---
title: "Firefox doesn't load"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by JRuc33 on 2009-05-24
So, I'm an absolute noob with xubuntu, and I'm running it on the ps3.  To save some memory, I ended a bunch of python processes in the system manager thing.  Now, even after restarting, firefox doesn't load.  If I try to install it again using Synaptic Package Manager I get this error 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
"E:_cache->open() failed, please report."

---

### Post by lisati on 2009-05-24
From the terminal (Applications->accesories->terminal) type in the following: ```
sudo dpkg --configure -a
```
It will ask for your password, which won't show as you type: just type in your normal password

---

