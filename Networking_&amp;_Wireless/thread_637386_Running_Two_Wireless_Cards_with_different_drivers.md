---
title: "Running Two Wireless Cards with different drivers"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by ASchweitzer on 2007-12-10
After many long nights of learning how to use ndiswrapper, and *finally* getting it to run my Atheros AR5007EG, I discovered that the ndiswrapper-supported windows driver doesn't support raw-monitor mode. I, however, really want to use raw-monitor mode, and, therefore bought a D-Link WNA 2330 (supported by the madwifi driver, which supports raw-monitor mode).

Unfortunately, problems arose when trying to plug in my cardbus D-Link card. My system froze and I had to hard boot to unfreeze it. After much investigation, and, out of curiosity, running my kernel in recovery mode from GRUB, I discovered than when I plug in my new D-Link WNA 2330, it creates a kernel panic.
I believe this may have something to do with ndiswrapper being loaded as part of the kernel, and being unable to run the D-Link  card.
Also, I have botoed from my live-CD, and the D-Link wifi card worked fine, as ndiswrapper isn't installed, further evidence to my theory that I have some sort of device/driver conflict going on.

Thus, my question becomes:
Provided that there isn't a way to run ndiswrapper for one device (my built-in Atheros AR5007EG), alongside madwifi for another (the D-Link WNA2330, which also uses a Atheros chip) is there a way to disable ndiswrapper after the kernel has loaded, but without removing it from the kernel; or is there a way to not load ndiswrapper for a different user? Basically I want to end up being able to use both cards at the same time, or at least choose which one to use after booting into Ubuntu.

BTW, I'm running Ubuntu 7.10 64 bit

Thanks in advance

Edit:
Just tried to```
sudo modprobe -r ndiswrapper
```I didn't get any response so I figured it worked, as modprobe usually only spits out errors. Alas, upon reboot, ndiswrapper still loaded and subsequently caused a kernel panic when  I plugged in my D-Link WNA2330

---

