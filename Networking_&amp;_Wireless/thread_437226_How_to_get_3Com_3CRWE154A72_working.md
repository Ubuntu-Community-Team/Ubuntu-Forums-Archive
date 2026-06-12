---
title: "How to get 3Com 3CRWE154A72 working"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by DrScum on 2007-05-08
from the forum I take that I need ndiswrapper which apparently is a tool to make the card work using the windows drivers. I hope I got that part right. Now, where do I get this ndiswrapper and how do I go about installing it and the driver.

---

### Post by chili555 on 2007-05-08
I believe this uses the Atheros chipset, which is supported by linux-restricted-modules which you can install by opening a terminal and:```
sudo apt-get install linux-restricted-modules
```Your interface, probably ath0, should appear, ready to be configured. I would certainly try this before I tried ndiswrapper.

---

