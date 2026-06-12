---
title: "Can I rename my wifi info?"
date: 2016-11-12
forum: Networking &amp; Wireless
---

### Post by rickblacker on 2016-11-12
All,
I have two WIFI cards in my computer. 

Card 1: PCI - A D-Link wifi card. My best performing internet card
Card 2 : USB - Poor wifi performance, but its a combo wifi and bluetooth card.

Is there a way that I can put some kind of a name on them in some config file somewhere, such that when I go into Settings -> Network, I can easily identify which card is which by name and not a long numerical value separated by : characters?   Would make it easier when i'm changing network settings ( work related ).  

Thanks

---

### Post by QIII on 2016-11-12
Hello!

It might be helpful if you could tell everyone which release you are using, since the answer may depend somewhat on that.

Are you talking about changing how you manage it on your machine, or how the machine appears to others on the network?

Cheers!

---

### Post by SeijiSensei on 2016-11-12
Usually they will already be named wlan0 and wlan1.  Do you need some other name?

---

### Post by QIII on 2016-11-12
Unless, of course, you are using 16.04 or beyond with systemd's predictable network device names (aka: Predictable Network Interface Names, Predictable Network Interface Device Names, etc).

:)

Things just have to be confusing!

---

### Post by SeijiSensei on 2016-11-12
I'm rather glad that my servers on CentOS 7 still use names like eth0 even though they are running systemd.

---

### Post by jeremy31 on 2016-11-12
It might be easiest to just blacklist the module for the USB wifi card.  Please post results for ```
lsusb; lsmod | grep mac80211
```

---

