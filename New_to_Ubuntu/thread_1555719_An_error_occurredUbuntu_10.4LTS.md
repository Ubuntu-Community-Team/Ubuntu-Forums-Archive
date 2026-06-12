---
title: "An error occurred:Ubuntu 10.4LTS"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by badaveil on 2010-08-18
I tried to update my Ubuntu but got this message:

E: /var/cache/apt/archives/libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb: trying to overwrite '/usr/share/java/swt.jar', which is also in package libswt-gtk-3.5-java 0

I tried to fix broken thing but unsuccessful. Any terminal command to solve this problem? Thanks

---

### Post by blazemore on 2010-08-19
```
sudo dpkg --configure -a; sudo apt-get -f install; sudo apt-get update
```

---

### Post by badaveil on 2010-08-20
> **blazemore said:**
> ```
sudo dpkg --configure -a; sudo apt-get -f install; sudo apt-get update
```

Wow, fast reply! Thank you very much.

---

