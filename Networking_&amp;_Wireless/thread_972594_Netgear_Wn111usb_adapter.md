---
title: "Netgear Wn111usb adapter"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by 4077mash on 2008-11-05
is there a way that i can get my Wn111 usb adapter to work with ubuntu?

---

### Post by pytheas22 on 2008-11-05
If you mean the WPN111, I think that it should work out-of-the-box on Ubuntu 8.10, although you shouldn't quote me on that.  So the easiest thing to do would be to upgrade to 8.10, if possible.

Otherwise, please post the output of the following commands (make sure your card is plugged in) and I will try to point you in the right direction:
```

lsusb
lshw -C Network
lspci -nn
```

---

