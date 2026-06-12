---
title: "HP Pavilion a6152n network"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by jongwoolee on 2007-08-15
Hi,

I'm trying to install the latest Ubuntu release on the HP Pavilion a6152n desktop. It doesn't seem to recognize the ethernet connection! (Windows will connect fine to the internet). Anyone have any suggestions?

Motherboard is IPIBL-LA from Asus with an integreated 10/100/1000 Base-T networking interface...

Thanks in advance.

---

### Post by noob12 on 2007-08-15
Posting these will provide information about the actual device and whether any driver has claimed it
```

lspci -nn

sudo lshw -C network

```

---

