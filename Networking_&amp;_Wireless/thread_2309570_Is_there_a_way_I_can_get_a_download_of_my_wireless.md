---
title: "Is there a way I can get a download of my wireless driver?"
date: 2016-01-11
forum: Networking &amp; Wireless
---

### Post by lewis12 on 2016-01-11
I have read up on this a lot, and it comes down to when I start Lubuntu for the first time it will need to be connected to the router with an ethernet cable to be able to download the driver for my computer since it can't access the net wirelessly off the bat.

I don't have such a cable, so couldn't I just get a driver for Linux for my wireless card by downloading it from inside Windows, and then manually installing it into Linux to get me on the net so I can get the other drivers for my system and updates etc using the auto feature inside Lubuntu?
My computer is a Dell 1545 Inspiron laptop.

---

### Post by Hadaka on 2016-01-11
Hi,please open a terminal ctrl/alt/t then copy and paste..
```
lspci -n | awk '/14e/{print$3}'
```
post the output,
thanks.

---

