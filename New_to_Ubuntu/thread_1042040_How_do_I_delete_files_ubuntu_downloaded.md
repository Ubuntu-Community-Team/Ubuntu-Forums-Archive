---
title: "How do I delete files ubuntu downloaded?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Boris-- on 2009-01-17
Hi!

When I uninstalled Amarok, only a little space was freed, in spite of doing autoremove. When I reinstalled it, it didn't have to download nothing, so I guess its packages remained on my system. 

I am in dire need of free space on my HD. How can I remove simmilar packages that hang around? 

Thanks in advance.

---

### Post by Tim Sharitt on 2009-01-17
To clean out downloaded package files:
```
sudo apt-get clean
```

---

### Post by sandip26879 on 2009-01-17
try the command sudo apt-get autoremove if you have done apt-get uninstall.

---

### Post by binbash on 2009-01-17
sudo apt-get autoclean

---

