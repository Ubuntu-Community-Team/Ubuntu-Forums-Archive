---
title: "cant download packages"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by endtheembargo on 2008-12-30
When I run the package/download manager I keep getting this error message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

I don't know what that means or what to do! Help please!

---

### Post by amauk on 2008-12-30
Open up a terminal, and type

```
sudo dpkg --configure -a
```

---

### Post by endtheembargo on 2008-12-30
ahhh sudo! of course! thank you :)

---

### Post by Michael.Godawski on 2008-12-30
hi, 

If you want to learn more about sudo visit the 
Introduction to Root and Sudo course presented by the Education Focus Team.

See my signature.

---

