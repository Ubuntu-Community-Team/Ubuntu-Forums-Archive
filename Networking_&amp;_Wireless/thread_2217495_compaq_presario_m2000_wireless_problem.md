---
title: "compaq presario m2000 wireless problem"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by Robert_Turner on 2014-04-17
does anybody know how to install conexant wireless drivers for the presario m2000 I am running ubuntu 12.04.

Thanks

---

### Post by varunendra on 2014-04-19
Most of the drivers are already included with the kernel and not needed to be installed from an external source. To by able to tell if your card really needs an external driver, we need to see its exact chip ID.

Is it a modem or a WiFi card? Internal or USB (or PCMCIA)?

To give us more details about the card/adapter, please open a terminal (Ctrl-Alt-T) and post back the outputs of following commands -
```
uname -mr
lsusb
lspci -nnk | grep -iA2 net
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

