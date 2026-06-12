---
title: "my terminal stopped functioning"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-08-06
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I got the above error message
how do I get the terminal back?
thanks

---

### Post by jmszr on 2009-08-06
Duke Togo,

In the terminal (Applications > Accessories > Terminal), type (or copy and paste)```
sudo dpkg --configure -a
```
When it asks for your password, type it (it won't be visible-security) and press enter.

---

### Post by Duke Togo on 2009-08-06
thanks

---

