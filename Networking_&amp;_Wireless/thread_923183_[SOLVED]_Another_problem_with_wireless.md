---
title: "[SOLVED] Another problem with wireless"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by gallumbits on 2008-09-18
Hi everyone,

I'd be really happy if someone could help me.
I have a Sony VAIO NR330E with Ubuntu installed. Everything works like a charm, except for the wireless...I just can't get it running.


At first I was using 8.04 - "Hardware drivers" detected and install Atheros HAL support and showed it as "in use", but no wireless.
Tried using ndiswrapper, but found no working drivers. I also installed MadWifi, following all the instructions but no wlan0 was found when I did ```
"ifconfig -a"
```

Also when i do lsmod | grep ath:
```
vasil@vaio:~$ lsmod | grep ath
ath_pci               216632  0 
wlan                  240880  1 ath_pci
ath_hal               312288  1 ath_pci
```

sudo modprobe ath-pci doesn't show any errors.

Currently I upgraded Ubuntu to the latest 8.10 alpha available and the Hardware Drivers shows "Support for Atheros 802.11 wireless LAN cards." - "This driver has just turned off, but is still in use". And when I click Install and Turn On nothing happers. I have attached a screenshot of it.

Oh, yeah and one last thing - i found an older thread, about the same problem - [http://ubuntuforums.org/showthread.php?t=855969]("http://ubuntuforums.org/showthread.php?t=855969") but it wasn't helpful at all - just saying NR330e users should wait for the official 8.10 release.

Any help will be deeply appreciated.

P.S. This is my first post and I am a bit of a newbie, so please don't be too harsh on me :)

EDIT Solved using the latest madwifi drivers for SVN. Works only with kernel 2.6.27-4

---

