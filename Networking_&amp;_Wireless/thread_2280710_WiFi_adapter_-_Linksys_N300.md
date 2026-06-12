---
title: "WiFi adapter - Linksys N300"
date: 2015-06-01
forum: Networking &amp; Wireless
---

### Post by mebenson on 2015-06-01
Will the LINKSYS N300 wireless-N USB adapter work on ubuntu 14.04 LTS? If not, what wifi adaptes work on ubuntu?

---

### Post by mebenson on 2015-06-07
Any feedback? I've updated to 14.04 and it's still not allowing me to install it. Any advice?

---

### Post by kurt18947 on 2015-06-08
> **mebenson said:**
> Any feedback? I've updated to 14.04 and it's still not allowing me to install it. Any advice?

Is this a 'built-in' or USB adapter? If USB, could you run this command in a terminal and copy/paste the results?
```
lsusb
```

If 'built in' ```
lspci
``` 

The output of the above commands will look something like this. This is the ethernet chipset on this machine, it doesn't have wifi. 

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
```

We're looking for the line that most likely says "network controller". That's the wifi adapter. Linux doesn't care about the device's manufacturer, it cares about the chipset manufacturer.

Regarding a WiFi adapter that 'just works', Trendnet TEW-649UB (using Realtek's RTL-8192SU chipset) has been plug-n-play for me for some years. It's not the fastest out there - N 300 down 150 up - but a fast enough device that connects reliably is a more useful than the fastest thing around that won't connect. It's useful to have a 'works-every-time' network adapter in your bag of tricks anyway.

---

