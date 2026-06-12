---
title: "Static assignment of wlan0"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by ThreeLies on 2010-02-19
I recently updated my main version I was running by doing a entire re-install. Originally my drivers for my wireless cards ran as eth1 (b43 Broadcom) and wlan0 (rtl8187) wireless cards. After I upgraded system versions I find that instead they are using wlan0/wlan1, where wlan0 is my b43. It isn't that annoying but I am wondering if I can set my rtl8187 card to specially always have wlan0 device name?

---

### Post by Iowan on 2010-02-19
Dunno if it'll stick, but you can (probably) change the definitions in */etc/udev/rules.d/70-persistent-net.rules*.

---

### Post by ThreeLies on 2010-02-19
> **Iowan said:**
> Dunno if it'll stick, but you can (probably) change the definitions in */etc/udev/rules.d/70-persistent-net.rules*.

I tried that out putting this in etc/udev/rules.d/70-persistent-net.rules

> SUBSYSTEM=="net", ATTRS{address}=="00:xx:xx:xx:xx:xx", NAME="eth1"

Filtering out the mac address of it. Then went for a reboot and wlan0 renamed itself 'wlan0_rename' and wlan1 still existing was my rtl8187 card.

Any other ideas?

---

