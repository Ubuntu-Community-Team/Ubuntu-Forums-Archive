---
title: "WMP54GS v1.0 Wireless drops after screensaver"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by srafx on 2006-11-08
**Problem:**
My wireless seems to be working perfect until the screen saver comes on.  I did notice, it could come on and then if I use the computer slightly after, my wireless still works.  It seems when the computer has been on all night or for long periods of time with the screen saver, it drops my wireless.  To fix it, I always have to reboot and if I try to connect again through network manager, most of the time it just freezes my computer.

**Hardware:**
Wireless card: WMP54GS v1.0 - Wirless-G PCI Adapter with SpeedBooster

**Software:**
NetworkManager Applet 0.6.3 w/ bcm43xx driver
Speed 11 Mb/s (I wish this was faster too)

**Interface config:**
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

**Power management:**
Put display to sleep when computer is inactive for: Never
Put computer to sleept when it is inactive for: Never
Sleep type when inactive: Do nothing

**Ubuntu:**
Edgy eft 6.10
Gnome


If anyone knows what could be causing this please any suggestions I will try.

---

### Post by srafx on 2006-11-08
Today I did a few more tests and I found out that is is NOT the screen saver.  I disabled the screen saver and just turned off my monitors.  It seems that the symptoms are:
- wireless drops
- cant open system monitor (just sits with think icon for about 30 seconds)
- cant shut down, restart (can click the button but not window pops up to ask what i want to do)
- and a few other not important things dont open as well

This seems to happen when my computer is idle for a while?  I know its not hardware because this doesnt happen in windows (hate to say that)

let me know if anyone knows anything...

---

### Post by Mavvy on 2008-03-31
Check power management..

---

### Post by *g!t5^_)*(H on 2008-05-11
Exactly the same for me with hardy

:(

Is there a solution, instead of come back to Dapper ?

Thanks

Albert

---

