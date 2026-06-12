---
title: "Ethernet Network disconnected"
date: 2018-07-30
forum: Networking &amp; Wireless
---

### Post by neelakant on 2018-07-30
Hi Ubuntu Community,
I am using Ubuntu 14.04.5 LTS version in my laptop.
Ethernet Network status is found to be disconnected and there is no internet signal displayed inspite of cable being connected to the laptop.
Kindly help me in resolving the problem.

---

### Post by praseodym on 2018-07-30
Please show the outputs of
```

lspci -nnk
lsmod
cat /etc/resolv.conf
route -n
```

---

