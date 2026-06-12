---
title: "Routing traffic command not working"
date: 2021-08-01
forum: Networking &amp; Wireless
---

### Post by pipobravo on 2021-08-01
Hello;
I want to route traffic to 192.168.1.100, I have found the two commands below in an other post but non of them works, why ?

```
sudo route delete *
sudo route add 0.0.0.0 mask 0.0.0.0 192.168.1.100
```

---

### Post by him610 on 2021-08-01
Take a look at the man page for route - the examples for add and delete.
```
man route
```
After that you could show us your current routing table to provide some background info for the network SME who may ask for more.
```
route
```

---

