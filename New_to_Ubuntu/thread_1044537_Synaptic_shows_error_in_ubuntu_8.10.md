---
title: "Synaptic shows error in ubuntu 8.10"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by fahadrather on 2009-01-19
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by lykwydchykyn on 2009-01-19
> **fahadrather said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What happened when you ran the suggested command to correct the problem?

---

### Post by kellemes on 2009-01-19
Indeed you should run from terminal..
```
sudo dpkg --configure -a
```

---

### Post by fahadrather on 2009-01-19
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


i just updated ubuntu....can that be a trouble creator??

---

### Post by lykwydchykyn on 2009-01-19
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=231752](http://ubuntuforums.org/showthread.php?t=231752)

Sounds like you might have encountered the same bug.  They post some solutions in that thread, but I haven't encountered this problem so I can't vouch for them.

---

