---
title: "setting Slim as the default login manager"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by fremantle on 2011-05-16
hello

I have set slim as the default login manager. i uninstalled gdm and then installed slim. but now when i login it takes me to the command line login screen followed by a command line ubuntu.,, so how can i set slim to automatically start as my login manager?

---

### Post by sisco311 on 2011-05-16
Run:
```
sudo dpkg-reconfigure slim
```
and select slim as the default DM.

---

