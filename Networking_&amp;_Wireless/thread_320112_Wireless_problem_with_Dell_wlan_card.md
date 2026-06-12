---
title: "Wireless problem with Dell wlan card"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by Homicide on 2006-12-16
Hi. New to linux and all that. So far I've managed to get my Inspiron 1300 up and working with Gnome Edgy 0.10. My ethernet connection works flawlessly, however my wireless card is not working. I have bcmwl5a as perscribed by another page (the source I cannot link because I foolishly left my flash drive at my house.) and I have verified that my wireless card is enabled and functioning properly.

However, my problem is this:

```
     *network:1 DISABLED
description: Wireless interface
product: Dell Wireless 1470 DualBand WLAN
vendor: Broadcom Corporation
physical id: 3
bus info: pci@02:03.0
logical name: eth1
version: 02
serial: 00:14:a5:4d:02:bc
width: 32 bits
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bmc43xx multicast=yes wireless= IEEE 8 02.11b/g
```

Now, looking at it again as I had to hand-type it (on a secondary computer), I see that my driver is bmc43xx, which, according to previously gleaned information, should have been blacklisted in favor of bcmwl5a. The only problem is that I was not able to figure out how to do this, even with the assistance of various documentations. If anyone could assist me with blacklisting this driver (and anything else I should probably do), I would appreciate it.

Thanks in advance.

---

