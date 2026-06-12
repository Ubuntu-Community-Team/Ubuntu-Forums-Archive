---
title: "Can't boot after configuring wireless (MRV8k51)"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by sambram on 2006-11-27
Hi All! I thought I had victory in my clutches after months of trying to get my mrv8k51 (D-Link) wireless card to work under Dapper. 

I did so by removing the broken driver for my card packaged with Dapper, and manually adding ndiswrapper to /etc/modules (Thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=190726"))

Voila, I even got connected for a second there, and thought I'd restart for good measure. **Now I can't get past "checking root file system" at boot.** (Seems equivalent when I try recovery mode.)

Any advice?

Edit: Okay, in verbose-recovery-mode-boot, the last things shown before the hang are:
```
Code: Bad EIP value.
wlan0: vendor: 'Marvell 802.11 Driver'
wlan0: ndiswrapper ethernet device 00:0f:3d:0a:03:2e using driver mrv8k51, 11AB:1FA6: 1186:3B09.5.conf
wlan0: encryption modes supported: WEP, TKIP with WPA
ndiswrapper (set_essid:61): setting essid failed (C0010015)
[OK]
Adding 746980k swap on /dev/hda5. Priority:-1 extents:1 across:746980k
*Checking root file system...
```

---

### Post by FrodoB on 2006-11-27
What is the output of

lspci

Also what version of Ubuntu are you using?

---

