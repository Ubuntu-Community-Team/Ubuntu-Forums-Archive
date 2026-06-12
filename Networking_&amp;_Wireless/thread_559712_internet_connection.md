---
title: "internet connection"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by dsilvar on 2007-09-25
hi all,
I have just installed ubuntu 7.04 and i cannot get my internet connection to work.
There are 2 other computers in the house and they connect to the wireless connection without any problem. I have Win XP on those two.
I have a Linksys router and a wireless card that is being recognized by th OS...i think...it picks up the network ESSID.
any insights?
thanks
ray

---

### Post by noob12 on 2007-09-25
If you post the output of these commands, it will tell people what you have and allow some suggestions:
```

lspci -nn

sudo lshw -C network

iwconfig

sudo iwlist scan

```

---

