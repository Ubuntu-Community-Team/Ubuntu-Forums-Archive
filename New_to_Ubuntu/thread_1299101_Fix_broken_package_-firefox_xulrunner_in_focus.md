---
title: "Fix broken package -firefox xulrunner in focus"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by darkchest on 2009-10-23
I upgraded my ubuntu 6 to 8.04 using the upgrade tool. I encountered a lot of broken packages so i started uninstalling a lot of programs. The problem now is that xulrunner does not seem to uninstall. Other programs had the following errors "ubufox 0.5-ubuntu1, ubuntu desktop 1.102 and ubuntu.docs 8.06.1 failed to install or upgrade".

So i guess the question is how to fix broken packages (xulrunner in focus).

Thanks

---

### Post by yeats on 2009-10-23
```
sudo apt-get -f install
```

should fix any broken packages.  Give it a shot.

---

### Post by darkchest on 2009-10-23
I tried that and it worked but when i wanted to install firefox again, i got this error message at the end

E: /var/cache/apt/archives/xulrunner-1.9_1.9.0.14+build2+nobinonly-0ubuntu0.8.04.1_amd64.deb: conflicting packages - not installing xulrunner-1.9

---

