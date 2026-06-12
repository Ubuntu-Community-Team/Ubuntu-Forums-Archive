---
title: "Qualcomm Atheros wifi driver"
date: 2016-04-08
forum: Networking &amp; Wireless
---

### Post by gmehta2 on 2016-04-08
Hi, 
I recently bought Acer ASpre E15 laptop  and deleted the windows OS and installed Ubuntu 14.04 . I am not able to connect to WIFI, there are no visible wifi connections . Network controller is Qualcomm Atheros.

Please help

Best
Guneet Singh

---

### Post by chili555 on 2016-04-08
Which of several Atheros' is it? Please open a terminal and run and post:```
lspci -nnk | grep 0280 -A2
dmesg | grep ath
```

---

