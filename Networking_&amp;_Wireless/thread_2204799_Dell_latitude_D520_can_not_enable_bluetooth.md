---
title: "Dell latitude D520 can not enable bluetooth"
date: 2014-02-10
forum: Networking &amp; Wireless
---

### Post by emeryd17 on 2014-02-10
I have a dell latitude D520 bought it used with win7 and put ubuntu 12.04 64 bit and upgrade to 13.10. i have tried to use my bluetooth and i cant enable it. i have tried sudo apt-get install [COLOR=#000000]bcmwl-kernel-source and rebooted and no luck i have also installed bluetooth manager. any help would be great.
[/COLOR]

---

### Post by varunendra on 2014-02-11
Welcome to the forums emeryd17!

> **emeryd17 said:**
> i have also installed bluetooth manager

Which manager? BlueMan? (sudo apt-get install blueman)

The bcmwl driver you installed is for Broadcom Wireless cards, not for bluetooth. The bluetooth adapters don't need external drivers, every thing required is already present in the kernel.

To see which bluetooth device you have, an if a driver is associated with it, please post back the output of -
```
usb-devices
```

While posting the output, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

