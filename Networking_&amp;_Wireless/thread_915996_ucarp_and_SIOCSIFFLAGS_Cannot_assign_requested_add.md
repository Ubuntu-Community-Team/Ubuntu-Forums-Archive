---
title: "ucarp and SIOCSIFFLAGS: Cannot assign requested address"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by mattmann72 on 2008-09-10
I am trying to get ucarp working on a desktop running Ubuntu 8.04. However whenever I do /etc/init.d/networking restart I get the following error for every subinterface.
SIOCSIFFLAGS: Cannot assign requested address

This seems to prevent ucarp from starting correctly because the ifup scripts do not run correctly. Any idea on how to fix this?

---

