---
title: "Wifi refuses to connect to network on system boot"
date: 2018-06-27
forum: Networking &amp; Wireless
---

### Post by ricecake on 2018-06-27
Hi! I've been using Lubuntu 16.04 has my main driver on my office PC for sometime now, nearly everything works like it should with one minor problem, every time I boot up the system I can see the wifi network just fine I can't connect to it, the wifi icon will do the "connecting to network" animation but will just yield "disconnected from network" no mater how many times I try I get the same error. The only solution is unplug the Wifi adapter (is a USB thumb drive like), replug it and everything sorts out.

I've already tried the stick on my co-worker machine and it works perfectly fine (he's using Windows 7 tou).

This a minor annoyance but one I would like to solve, if anyone have some advice on the matter I would really appreciate.

---

### Post by praseodym on 2018-06-30
Please run the wireless script from the sticky thread and show the outputs

---

### Post by ricecake on 2018-07-03
Here you go[URL="http://paste.ubuntu.com/p/8fKXcmVTyF/"]

http://paste.ubuntu.com/p/8fKXcmVTyF/[/URL]

---

### Post by praseodym on 2018-07-03
Which country do you live? Check
```

lsmod
iwconfig
```
when its not working after boot

---

