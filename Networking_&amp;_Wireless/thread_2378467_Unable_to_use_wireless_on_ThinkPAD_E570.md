---
title: "Unable to use wireless on ThinkPAD E570"
date: 2017-11-23
forum: Networking &amp; Wireless
---

### Post by availero on 2017-11-23
Hello guys,
thank you for this thread [["]https://ubuntuforums.org/showthread.php?t=2371149]("https://ubuntuforums.org/showthread.php?t=2371149)] so far, it helped me alot. I got an E470 Lenovo, but still got some wifi issues.
After installing the driver like it was suggested here, the wifi card showed up and I could connect to Wifi-Networks. But somehow every 5 minutes the connection was lost, although Network Manager still showed a working connection.
So I got myself a cheap Wifi-Dongle and planed using it until offical drivers are released.
But somehow it's the exact same situation with the Dongle.
I'm also using Ubuntu 17.10 and I'm kinda clueless what to do now. I'd appreciate any suggestions.

---

### Post by kurt18947 on 2017-11-23
Which dongle did you get? Maybe post the results of "lsusb" in a terminal  to give an idea of the chipset used in the USB dongle. For instance, 

```
Bus 004 Device 002: ID 04d9:a0cd Holtek Semiconductor, Inc.
```

is my keyboard

A USB wifi device might be referred to as a 'network controller' or something like that.

---

