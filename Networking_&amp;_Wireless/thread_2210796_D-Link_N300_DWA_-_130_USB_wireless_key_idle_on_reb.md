---
title: "D-Link N300 DWA - 130 USB wireless key idle on reboot"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by nathanielbm8 on 2014-03-12
I'm using the USB wireless key mentioned in the title on Ubuntu 12.04 and I must say it works extremely fine, just plug and play, nothing to install, great connection. 

That is, until I reboot the computer. Then the light won't turn on and neither will the Wi-Fi. Lsusb tells that the key is connected. If I unplug the key, the computer crashes. 

Tried to force load a module called rtlwifi, not sure if it worked or if it's not enough. 

Any clue ladies and gents?


EDIT : Seems the problem is related to unknown crash. In 
A : Everything is fine 
B : crash or freeze, has to force restart 
C : wireless key does not work after that restart or any other afterward, as long as it stays plugged
D : When the key gets plugged in a working computer, works perfectly and as perfectly after any restart, as long as B does not repeat

So I guess the issue is unrelated, though a crash proof solution might be, I'll start by looking if those crashes are frequent or have an identifiable cause first. Thanks ubuntians!

---

### Post by praseodym on 2014-03-12
Which chipset and kernel is in use? Please show
```

uname -a
lsusb
```
Edit: Does LAN work?

---

### Post by nathanielbm8 on 2014-03-13
Wow, thanks for the quick answer!

Here is with the key working (LAN is working fine)

bm@bm-Satellite-L500:~$ uname -a
Linux bm-Satellite-L500 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
bm@bm-Satellite-L500:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8191SU]
bm@bm-Satellite-L500:~$


EDIT : Well, this is embarrassing, I wanted to give you the info when the key doesn't work, but I do restart and it seems it worked both time. No idea about how and why, maybe the trick I tried paid off, can't tell. Anyway, thanks a lot for trying to help and sorry for the bother!

---

