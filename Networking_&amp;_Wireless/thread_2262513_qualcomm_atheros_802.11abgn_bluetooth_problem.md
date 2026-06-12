---
title: "qualcomm atheros 802.11ab/g/n bluetooth problem"
date: 2015-01-25
forum: Networking &amp; Wireless
---

### Post by rahul30 on 2015-01-25
i have an acer e1-572. am usin ubuntu 14.10 and facing bluetooth problem, bluetooth firmware not loading
somebody please help..............!

---

### Post by jeremy31 on 2015-01-25
> **rahul30 said:**
> i have an acer e1-572. am usin ubuntu 14.10 and facing bluetooth problem, bluetooth firmware not loading
somebody please help..............!

Ok, let me see the results of ```
lspci -nnk | grep -iA2 net
```
```
lsusb
```
```
dmesg | grep firmware
```

What model number is the wifi card, it might be on the bottom of laptop

And ```
modinfo ath3k | grep alias
```

---

