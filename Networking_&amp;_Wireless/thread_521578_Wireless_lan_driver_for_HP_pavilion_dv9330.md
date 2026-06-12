---
title: "Wireless lan driver for HP pavilion dv9330"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by rishabhsagar on 2007-08-09
Hi,

    I tried to install the lan card driver from the previous threads , but nothing seems to work out.  I am a new convert to linux, and am still hanging onto windows, untill I get the wireless connection working on ubuntu.

>  How do I check the make of my wireless card on my laptop in ubuntu?
> How do I find a suitable driver for that card?

Regards!!

---

### Post by noob12 on 2007-08-10
This is for a PCI card (which the internal card will be).
```

lspci -nn

lshw -C network

```

Post these and someone will help point you to the drivers to use.

---

