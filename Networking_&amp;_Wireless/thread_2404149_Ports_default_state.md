---
title: "Ports default state"
date: 2018-10-20
forum: Networking &amp; Wireless
---

### Post by sky59 on 2018-10-20
I use Ubuntu 16.04LTS and need to know what ports are open/closed after fresh install.

I know port 22 is open because we can SSH pc with ubuntu. What about ports 443, 1193 and so on?

Thanx

---

### Post by DuckHook on 2018-10-20
Try:```
netstat -atun
```
Port 22 should not be open unless you installed ssh-server.
For better control over ports, use *ufw* or *gufw*.

---

