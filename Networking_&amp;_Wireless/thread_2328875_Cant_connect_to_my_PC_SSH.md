---
title: "Cant connect to my PC SSH"
date: 2016-06-25
forum: Networking &amp; Wireless
---

### Post by ksd2 on 2016-06-25
Hi.
I can connect to a friend's PC through SSH but he can't connect to mine.
We are connected to the same network on a WiFi.
Is my SSH port blocking incoming requests ?

---

### Post by jeremy31 on 2016-06-25
Post the output for ```
dpkg -l | grep ssh
```

---

### Post by ksd2 on 2016-06-25
[ATTACH=CONFIG]269773[/ATTACH]

---

### Post by jeremy31 on 2016-06-25
See if ```
sudo apt-get install openssh-server
```
Gets it working

---

