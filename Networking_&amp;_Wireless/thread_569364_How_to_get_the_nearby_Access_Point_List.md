---
title: "How to get the nearby Access Point List"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by apexlee on 2007-10-06
Hi all:
     I want to know which Acess Points are near my laptop, so how to do this ?
     Are there any API can do this ? or I can get the information from a file ?

---

### Post by MrFSL on 2007-10-07
From terminal

```
iwlist eth1 scanning
```

Note, replace eth1 with whatever your wireless adapter is. You can get this via:
```
iwconfig 2>&1 | grep 802.11
```

---

