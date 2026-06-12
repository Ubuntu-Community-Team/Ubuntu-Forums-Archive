---
title: "How can I get my Netgear WNDA3100v3 Wireless Adapter working in Ubuntu 14.04.3"
date: 2016-01-21
forum: Networking &amp; Wireless
---

### Post by jadenPete on 2016-01-21
Hello everyone! I have been given a WNDA3100v3 adapter, and I have it working in the Windows 7 side of my dual boot setup. However, I would like to get this working in Ubuntu too, because it is my favorite of the 2 OS's. Right now i'm stuck with a slow, tethered connection, while the adapter provides much better speeds. I have seen threads about previous versions, the WNDA3100v2 being the most common. Many have got those to work, but I am assuming the WNDA3100v3 is very new, so no drivers exist. It is based on Realtek/Mediatek and Ralink manufactures it, for those curious. I have tried loading the Windows drivers onto Ndiswrapper with no success. I would be very grateful if someone could point me to the right drivers to use or the right thing to do. By the way, I am not returning it, because I use it in Windows 7, as I said before. Thanks! :D

---

### Post by Vladlenin5000 on 2016-01-22
Hi and welcome.

Unfortunately there are no drivers for Linux (yet): [https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3)

---

### Post by deadflowr on 2016-01-22
Moved to Networking and Wireless

---

### Post by chili555 on 2016-01-22
> **jadenPete said:**
> Hello everyone! I have been given a WNDA3100v3 adapter, and I have it working in the Windows 7 side of my dual boot setup. However, I would like to get this working in Ubuntu too, because it is my favorite of the 2 OS's. Right now i'm stuck with a slow, tethered connection, while the adapter provides much better speeds. I have seen threads about previous versions, the WNDA3100v2 being the most common. Many have got those to work, but I am assuming the WNDA3100v3 is very new, so no drivers exist. It is based on Realtek/Mediatek and Ralink manufactures it, for those curious. I have tried loading the Windows drivers onto Ndiswrapper with no success. I would be very grateful if someone could point me to the right drivers to use or the right thing to do. By the way, I am not returning it, because I use it in Windows 7, as I said before. Thanks! :DPlease run and post:```
lsusb
```

---

