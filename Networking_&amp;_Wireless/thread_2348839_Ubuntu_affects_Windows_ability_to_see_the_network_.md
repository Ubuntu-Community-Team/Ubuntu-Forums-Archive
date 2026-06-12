---
title: "Ubuntu affects Windows ability to see the network card"
date: 2017-01-07
forum: Networking &amp; Wireless
---

### Post by tonma on 2017-01-07
I have a dual boot system: Ubuntu 16.04 with Windows 10 (64 bit)
I noticed that when I use Ubuntu and disable network or disable bluetooth, and then going to Windows, Windows will not be able to correctly recognize the network card:
It does appear in Device manager, but there is not way to make the network / bluetooth work (bluetooth won't even show up)

---

### Post by TheFu on 2017-01-08
I've seen issues reported with Realtek drivers doing something like this going to Linux from Windows. What hardware/chips are causing the issue?
**sudo lshw -C network** will show us. Please post with **code tags**.

---

