---
title: "BGH Positivo AT 300 Wireless &amp; Bluetooth Problem"
date: 2019-03-20
forum: Networking &amp; Wireless
---

### Post by ragallo on 2019-03-20
Hi, 

I install Lubuntu 18.04 and I have problems with the PCI, it's not recognized.

Here is the info of the script in the post with the [information ]("http://paste.ubuntu.com/p/bJ2Zrq5tzX/")

I try to reinstall Lubuntu, but the problem persist. 

Tnks.

---

### Post by praseodym on 2019-03-21
> ```
r8723bs
```
Looks like an SDIO card?!

```
cat /sys/bus/sdio/devices/*
cat /sys/bus/sdio/devices/*/uevent
dmesg | grep r8
```

---

