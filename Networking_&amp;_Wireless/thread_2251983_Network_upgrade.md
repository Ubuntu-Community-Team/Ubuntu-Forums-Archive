---
title: "Network upgrade"
date: 2014-11-08
forum: Networking &amp; Wireless
---

### Post by mayagrafix on 2014-11-08
During upgrade to 14.10 a message box came up asking if I wanted to keep the original wi-fi network or replace it. since it was already working, I chose the keep original network option. should I now upgrade the network with apt-get?

---

### Post by Bucky Ball on 2014-11-08
*Thread moved to **Networking & Wireless**.*
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

See how that goes. Then check 'Additional Drivers'.

---

