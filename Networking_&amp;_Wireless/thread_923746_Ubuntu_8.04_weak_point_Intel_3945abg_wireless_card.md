---
title: "Ubuntu 8.04 weak point Intel 3945abg wireless card"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by danmif on 2008-09-18
:(

many are those who expieriance problems with no wifi after instaling the latest version of ubuntu the problem is that i'm tryng to solve it but i feel that i'm stuck .what can we do for this problem???

---

### Post by pytheas22 on 2008-09-18
What's wrong exactly?  Do you have no wireless interface at all?  Can you see networks but not connect?

Please also provide the output of:
```

lspci -nn
lshw -C Network
dmesg | grep -e iwl
modinfo iwl3945
```

---

