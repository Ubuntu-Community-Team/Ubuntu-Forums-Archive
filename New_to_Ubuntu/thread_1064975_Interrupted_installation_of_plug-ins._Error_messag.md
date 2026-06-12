---
title: "Interrupted installation of plug-ins. Error message"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by anthonyleamy on 2009-02-09
Hello, :)
am new to Linux, but love what I have seen so far.  
I received the following message while installing flash plug-ins. How should I proceed? 
 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thank you

---

### Post by Nepherte on 2009-02-09
The error message already tells you what to do:
```
sudo dpkg --configure -a
```

---

### Post by anthonyleamy on 2009-02-09
Thank you. Worked a treat. Easy when you know how!

---

