---
title: "How do I add extra moden initialisation commands to my modem on the new ubuntu 7.10"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by davidgutu on 2007-12-27
How do I add extra moden initialisation commands to my modem on the new ubuntu 7.10?

Thanks in advance

---

### Post by anubhavrocks on 2007-12-27
suppose you are using ppp0
The init commands are in > /etc/chatscripts/ppp0 

---

### Post by anubhavrocks on 2007-12-27
An easier way is using kppp
```
sudo apt-get install kppp
```

---

