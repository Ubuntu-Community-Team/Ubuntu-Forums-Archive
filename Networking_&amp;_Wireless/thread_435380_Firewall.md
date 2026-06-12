---
title: "Firewall"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by aerotheexiled on 2007-05-06
Does ubuntu have a firewall or something similar that monitors connections? If so how do i turn it off? thanks

---

### Post by MRiGnS on 2007-05-06
It's built into the kernel

```
man iptables
```

for the manual

```
sudo apt-get install firestarter
```

for a GUI

---

