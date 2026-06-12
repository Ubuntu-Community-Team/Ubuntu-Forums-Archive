---
title: "Cant open port 80"
date: 2016-03-19
forum: Networking &amp; Wireless
---

### Post by astarmathsandphysics on 2016-03-19
I have opened port 80 in router and ufw, and netstat -ntlp | grep LISTEN tells me apache2 is listening on port 80. Still port 90 is not open externally. This has been so for two days and I cant fix it.
Any ideas?

---

### Post by astarmathsandphysics on 2016-03-19
Other ports - 25,465,993, 587 - are open ok

---

### Post by astarmathsandphysics on 2016-03-19
Fixed it by reinstalling apache2

---

