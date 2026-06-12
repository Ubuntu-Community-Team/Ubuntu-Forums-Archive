---
title: "network folder after 16.04"
date: 2021-03-01
forum: Networking &amp; Wireless
---

### Post by starpaly on 2021-03-01
Since Ubuntu now uses netplan is the network folder still necessary?

---

### Post by chili555 on 2021-03-01
Do you mean the file /etc/network/interfaces? Yes, it is necessary. Mine reads, for example:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d

```

---

### Post by starpaly on 2021-03-02
Funny, after upgrading to 20.04 my network folder is empty?

---

