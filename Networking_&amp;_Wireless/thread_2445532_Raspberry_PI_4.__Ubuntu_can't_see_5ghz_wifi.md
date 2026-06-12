---
title: "Raspberry PI 4.  Ubuntu can't see 5ghz wifi"
date: 2020-06-15
forum: Networking &amp; Wireless
---

### Post by kgonepostl on 2020-06-15
My localization is set correctly, but for some reason I can't see 5ghz networks.  I'm a n00b with Ubuntu, but I'm fairly confident I can provide you what you need.  All apps updated via sudo apt update && sudo apt upgrade.  I have no idea why this is. With raspbian I can connect to 5ghz, no problem.  It's a Raspberry Pi 4gb, with ubuntu core 20 installed.  I hate 2.4ghz, please help!!

---

### Post by kgonepostl on 2020-06-15
Anybody??  2.4 ghz sucks ass, and I have no idea where to start.  I appreciate anybodies input at this point.  Localization options should have fixed this after a restart of the PI, but I still can't connect to my 5ghz band, as I can't see it.  Thanks!!

---

### Post by Yuioup on 2020-06-17
It's probably your channel. Check your router settings. For example my Wifi adaptor on Windows can't see it if the channel is too high. Pick the lowest setting and see if it helps.

---

### Post by kgonepostl on 2020-06-17
> **Yuioup said:**
> It's probably your channel. Check your router settings. For example my Wifi adaptor on Windows can't see it if the channel is too high. Pick the lowest setting and see if it helps.
But I can connect to 5ghz using the same channel in Raspbian.  Wouldn't that be a hardware thing??

---

### Post by chili555 on 2020-06-17
> **kgonepostl said:**
> But I can connect to 5ghz using the same channel in Raspbian.  Wouldn't that be a hardware thing??Indeed it could. The hardware in one is very probably different from the other. From the one that *doesn't* get 5 gHz, please run and post:

```
sudo iwlist chan
```

From the other, find out and tell us the channel you are unable to see.

---

### Post by kgonepostl on 2020-06-17
> **chili555 said:**
> Indeed it could. The hardware in one is very probably different from the other. From the one that *doesn't* get 5 gHz, please run and post:

```
sudo iwlist chan
```

From the other, find out and tell us the channel you are unable to see.
I need to dispel some confusion.  It's one device, a Raspberry Pi 4 4GB running the latest Ubuntu Core.  It can connect to 5ghz in Raspbian, but not in Ubuntu Core.   I'm out of town for the next 2 days.  I'll post when I can with that command.  I'll also try lowering the channel while I'm at it.

---

### Post by kgonepostl on 2020-06-21
Alright, I lowered the band from 161 to 48, and the 5ghz wifi shows up now.  Weird...............

---

