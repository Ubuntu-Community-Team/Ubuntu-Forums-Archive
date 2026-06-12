---
title: "first time with ubuntu"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by koloth22 on 2008-08-06
I have a gigabyte wireless card in a dell dimension desktop system. I put ubuntu on it because my girlfriend went crazy over this OS. I don't know where to go to connect to wireless or to see if the driver works or not.

---

### Post by pytheas22 on 2008-08-06
Please open up a terminal (Applications>Accessories menu), run these commands and post the output here:
```

lspci -nn
lsusb
lshw -C Network
uname -m
```

so that we'll know what kind of wireless card you have and can find instructions on how to make it work on Ubuntu.

---

