---
title: "RTL8168 Issues"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by monkey89 on 2008-08-26
Hi,

I have Hardy installed with a custom 2.6.26 kernel (I've tested with the LiveCD version and had the same problems).  My network card, an RTL8168, only works on a sporadic basis - on most boots, I'll see messages like this in dmesg:
```

rtl8168: eth0: link down

```
Even when the internet does come on, I can't suspend or reboot the computer because it often will not be back upon resume.  Sometimes, it seems like Linux screws with the adapter, because when I boot into Windows it still will not work until I reboot again.

I tried using the latest driver from Realtek's website for r8168 and I removed all traces of the r8169 driver from the system, but that doesn't seem to do it.  The pci=nomsi boot option doesn't seem to consistently fix it either.  Does anyone have any other ideas?

---

### Post by Milv8 on 2008-08-26
Hi There
have a look at this sticky.
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
i was having the same problem as you described. read the section on the rtl network card, i just black listed as described and problem fixed.

regards
milv8

---

