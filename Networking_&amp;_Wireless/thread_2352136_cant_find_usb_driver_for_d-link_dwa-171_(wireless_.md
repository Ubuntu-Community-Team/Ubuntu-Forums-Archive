---
title: "cant find usb driver for d-link dwa-171 (wireless AC dual band USB adapter)"
date: 2017-02-09
forum: Networking &amp; Wireless
---

### Post by hyburn on 2017-02-09
can anyone help me find the driver for this? my TP-link is dying FAST

---

### Post by hyburn on 2017-02-09
this worked for me
```

sudo apt-get install git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au

```

---

### Post by Bucky Ball on 2017-02-09
Great news. Please see the last link in my signature to mark the thread as solved an help others.

Enjoy. ;)

---

