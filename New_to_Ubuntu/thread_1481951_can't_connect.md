---
title: "can't connect"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by qq0800 on 2010-05-13
carelessly,I removed something,by the command"apt-get remove ppp",and ubuntu can't connect.
So I downloaded ppp from ftp,and installed it.But it still don't work.

---

### Post by ukripper on 2010-05-13
Use this comamnd to install again:
```
sudo apt-get install ppp
```

---

### Post by moep on 2010-05-13
> **qq0800 said:**
> carelessly,I removed something,by the command"apt-get remove ppp",and ubuntu can't connect.
So I downloaded ppp from ftp,and installed it.But it still don't work.

If you can no longer access the internet from that particular machine because ppp is missing, you can download the package from a mirror (as you already did), put it on a USB drive and install it using ```
dpkg -i packagename
```.

---

### Post by qq0800 on 2010-05-13
i have install "ppp",but it still dont work

---

