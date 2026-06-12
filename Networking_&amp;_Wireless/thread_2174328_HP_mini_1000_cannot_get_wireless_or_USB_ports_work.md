---
title: "HP mini 1000 cannot get wireless or USB ports working (12.04)"
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by Spunks3 on 2013-09-13
When i go to activate the wireless drivers i get an error about a joggy,log.  im new to this, hoping someone can help

---

### Post by Hadaka on 2013-09-13
Hi, please post the output of..
```
lspci -nnk | egrep '0200|0280'
lsmod
lsusb
rfkill list 
```
thanks.

---

