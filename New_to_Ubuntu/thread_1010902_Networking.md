---
title: "Networking"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by sctt.reid on 2008-12-14
I am new to Linux and for some reason my wireless internet isn't working. The wireless card is an atheros AR5007EG wireless network adapter. Any help is greatly appreciated

---

### Post by karlsomewhat14 on 2008-12-14
Try this out: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by Michael.Godawski on 2008-12-14
Yes, you can follow the instructions posted above.

Additionally please post the output of these terminal commands:

```
sudo lshw -C network
iwconfig
```

after the first one you will have to enter your login/sudo password, it won't be displayed just type it in and hit enter.

---

### Post by sctt.reid on 2008-12-14
Michael I tried typing in what you told me to but it simply replied sudo doesn't recognize that command.

---

