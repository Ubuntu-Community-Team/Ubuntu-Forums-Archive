---
title: "modprobe: FATAL: Module wl not found (Intel 3160 wireless)"
date: 2018-01-04
forum: Networking &amp; Wireless
---

### Post by domwoolf on 2018-01-04
My Wireless network suddenly stopped working. I'm using Kubuntu 17.04 (on a dual-boot windows 10 machine - wireless works fine on Windows, so not a hardware issue). 

sudo modprobe wl gives the following error.
modprobe: FATAL: Module wl not found in directory /lib/modules/4.10.0-42-generic

I've seen previous threads describing this error with a Broadcom wireless card ([here]([https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)) and [here]([https://ubuntuforums.org/showthread.php?t=2348654](https://ubuntuforums.org/showthread.php?t=2348654))), but the solutions there do not work for me, because I have an Intel 3160 wireless

Pastebin link for network script is [https://paste.ubuntu.com/26322902/](https://paste.ubuntu.com/26322902/)

Very grateful for any  help

---

### Post by chili555 on 2018-01-04
In your paste, in the Network Manager settings, it reports, &#8220;Wireless Enabled: False.&#8221; Will you please click the Network Manager icon and enable it? [https://images.techhive.com/images/article/2014/07/ubuntu-networkmanager-menu-100360176-large.png](https://images.techhive.com/images/article/2014/07/ubuntu-networkmanager-menu-100360176-large.png)

*wl* is not correct for your Intel, so please abandon it.

---

### Post by domwoolf on 2018-01-05
Thank you chili555.  I was not able to enable the wireless previously, hence my post.  But now it seems to work.  I have no idea why it was not working before and is now.  Should I delete this thread as it does not seem very useful to others, or should we just mark it as solved?

Thanks again

---

