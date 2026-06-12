---
title: "How to auto logoff terminal screen"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by rohan2k10 on 2010-07-14
Hi, 

how can I auto logoff an idle terminal screen if its been idle for 2 mins. I am using 64-bit Ubuntu Server 10.04. Telnet etc shd work, it shd only logoff the terminal so that noone else gain access to the server.

Please help.

Thanks.

---

### Post by rohan2k10 on 2010-07-15
Any Solution????

---

### Post by jtarin on 2010-07-15
[Could be a solution for you to lock the screen]("http://smallboxadmin.blogspot.com/2008/10/adding-lightweight-gui-to-ubuntu-server.html")

---

### Post by sisco311 on 2010-07-15
If you are using bash, set the TMOUT environment variable to 120.

~/.bashrc:
```
...
TMOUT=120
```

---

### Post by rohan2k10 on 2010-08-04
Thanks aton for your help.

---

