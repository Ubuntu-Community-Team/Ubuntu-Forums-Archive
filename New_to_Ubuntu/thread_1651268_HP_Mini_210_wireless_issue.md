---
title: "HP Mini 210 wireless issue"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by NuCross on 2010-12-22
Wireless on my Mini 210 isn't working
how would i fix that?? :\
thanks =P

---

### Post by pytheas22 on 2010-12-22
Please open a terminal from the Applications>Internet menu, type the following commands (one per line) and paste the output here.  This will provide the information we'll need to figure out how to solve your problem:
```

lspci -nn
lsusb
lshw -C Network
uname -a
sudo iwlist scan
dmesg | grep -e b43 -e iwl -e rtl -e wlan
```

---

