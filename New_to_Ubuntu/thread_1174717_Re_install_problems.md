---
title: "Re: install problems"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by chamarams on 2009-05-31
i try to install C++ in kubuntu fallowing code
sudo apt-get install g++ 
but i can't install it's gave this bug 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correctthe problem.

please help me

---

### Post by Sef on 2009-05-31
1) Moved to its own thread.

2) Run this command from the terminal:

```
kdesu dpkg --configure -a
```

---

