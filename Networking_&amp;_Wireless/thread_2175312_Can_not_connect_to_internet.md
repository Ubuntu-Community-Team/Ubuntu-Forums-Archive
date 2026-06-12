---
title: "Can not connect to internet"
date: 2013-09-18
forum: Networking &amp; Wireless
---

### Post by Chetan_Mhatardeo_Khandave on 2013-09-18
Sir, I recently install ubuntu on my laptop acer Aspire 4520, But I can not get connect to Internet by wired connection. Please help me.

---

### Post by Hadaka on 2013-09-18
Hi, please Copy and paste the following..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list
```
post the output.
thanks.

---

