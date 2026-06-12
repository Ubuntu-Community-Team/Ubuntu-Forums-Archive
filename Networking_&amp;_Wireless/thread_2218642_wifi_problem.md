---
title: "wifi problem"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by neeraj5 on 2014-04-21
i just updated ubuntu 12.04 LTS but after updating my wifi is not working. i m using dell inspiron 3437. please help me

---

### Post by praseodym on 2014-04-21
Please show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

