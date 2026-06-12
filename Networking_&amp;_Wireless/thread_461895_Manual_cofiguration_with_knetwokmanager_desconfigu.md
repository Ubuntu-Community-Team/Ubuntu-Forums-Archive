---
title: "Manual cofiguration with knetwokmanager desconfigure my /etc/hosts file"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by parrusete on 2007-06-02
Well, the title resume my problem, every time I do manual configuration of the network using Knetworkmanager, I get my /etc/hosts file desconfigure...like this

The first line should be that --> 127.0.0.1 localhost.localdomain acer
instead I got that one           --> 127.0.0.1 localhost.localdomain

so every time I try to do "sudo" I cant, getting this message --> sudo: unable to lookup acer via gethostbyname()

then I have to log in like root and change my /etc/hosts file manually.

I hope someone can give me a tip of whats going wrong.
Thanks k/ubuntusers!

---

### Post by chili555 on 2007-06-02
Here is an abbreviated version of my /etc/hosts if it helps you:```
chili@LAPTOP60:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       LAPTOP60
```

---

