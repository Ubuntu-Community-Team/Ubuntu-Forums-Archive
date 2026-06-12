---
title: "Cannot enable Broadcom 802.11 Linux STA wireless driver source"
date: 2018-08-29
forum: Networking &amp; Wireless
---

### Post by aidencgg on 2018-08-29
Hey,

I'm trying to enable wireless on my Xubuntu, and I think everything is in place. However, when I go to "Additional Drivers" and attempt to change my wireless status from "Do not use this device" to "Using Broadcom", it changes back to do not use when I try to apply it. Am I missing something?

Happy to use terminal,
-Aiden

---

### Post by chili555 on 2018-08-29
Let's start by identifying the hardware in question. Please run and post:```
lspci -nnk | grep 0280 -A3
rfkill list all
```Thanks.

---

