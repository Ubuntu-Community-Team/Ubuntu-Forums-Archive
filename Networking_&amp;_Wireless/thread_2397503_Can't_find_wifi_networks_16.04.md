---
title: "Can't find wifi networks 16.04"
date: 2018-07-30
forum: Networking &amp; Wireless
---

### Post by kiraasht on 2018-07-30
I have had no trouble using wifi on ubuntu 16.04 until a few days ago I turned on my computer and it could no longer find my home wifi network, or any other network. I can connect to the internet tethered to my phone but wireless has just disappeared. Thoughts?

---

### Post by chili555 on 2018-07-30
Please open a terminal and run and post:```
uname -r
lspci -nnk | grep 0280 -A3
```Thanks.

---

