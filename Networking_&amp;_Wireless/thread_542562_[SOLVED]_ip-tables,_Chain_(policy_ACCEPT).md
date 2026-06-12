---
title: "[SOLVED] ip-tables, Chain (policy ACCEPT)"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by olavjunior on 2007-09-04
Earlier I opened a port for torrent, but when I was going to check witch one, ```
sudo iptables -L
```

I got this output:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```

Does anybody know why and what this means?

---

### Post by noob12 on 2007-09-04
This means you have no iptables filter rules whatsoever and that the default policy is to ACCEPT on each of those chains.  In other words, nothing is blocked or treated specially at all.

To check ports where you are listening type:
```

netstat -tnl

```

---

### Post by olavjunior on 2007-09-09
Hm, that sounds unsafe!  Is it?

---

