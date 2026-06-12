---
title: "How to get to the desktop"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by twilliamswithaz on 2008-12-18
Hello. I just installed 8.10, upgrading from my ubuntu server 8.4 version. i added the 8.10 kernal and the desktop. however, i don't know how to access the desktop.

---

### Post by hellion0 on 2008-12-18
If you have a bash prompt and no GUI, try...
```
sudo gdm
```if you installed ubuntu-desktop or xubuntu-desktop, or ```
sudo kdm
``` if you installed kubuntu-desktop. Either one of those should try to start X and bring up the GUI. You'll have to log in again when prompted, but then you should be able to get into the desktop.

---

