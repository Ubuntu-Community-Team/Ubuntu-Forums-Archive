---
title: "error when updating. dpkg file"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-03-14
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

this comes up when i go to update!! how do i fix?

---

### Post by drs305 on 2009-03-14
```
sudo dpkg --configure -a
```

It will ask for your password. You won't see it as you type for security reasons.

---

### Post by cirabisi2009 on 2009-03-14
thanks a bunch!!

---

