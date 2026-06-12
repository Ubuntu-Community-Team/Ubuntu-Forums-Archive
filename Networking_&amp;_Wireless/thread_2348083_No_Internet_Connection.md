---
title: "No Internet Connection"
date: 2016-12-31
forum: Networking &amp; Wireless
---

### Post by sacxyam1 on 2016-12-31
Just intalled ubuntu 16.04.01 LTS on my Sony Vaio Laptop. The Wifi is connected and I can ping google but cant use/browse firefox and download apps. It says there is no internet connection.

---

### Post by praseodym on 2016-12-31
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk
lsmod
rfkill list
```
C/P the output into a textfile and upload it

---

