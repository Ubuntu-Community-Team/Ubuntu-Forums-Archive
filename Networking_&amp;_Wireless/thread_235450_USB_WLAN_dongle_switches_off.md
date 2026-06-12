---
title: "USB WLAN dongle switches off"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by Nehemiah on 2006-08-13
I am having trouble with a USB WLAN dongle (sold locally in New Zealand as a DSE XH8344) running as rausb0. It seems to die periodically and never starts up after my box hibernates -- I suspect it's being switched off for power saving and not switched on again.

I am manually setting it up using /etc/network/interfaces as the Ubuntu networking GUI doesn't work with it (as has been discussed elsewhere on these forums). I get it working with the following:

> iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
pre-up ifconfig rausb0 down
pre-up iwconfig rausb0 essid ****
pre-up iwconfig rausb0 key **********
pre-up dhclient rausb0
auto rausb0

I tried adding the following line to switch off power management for the dongle: 

> pre-up iwconfig rausb0 power off

However, this stopped the dongle from working altogether. So I suspect I'm doing something wrong.

Anyone else encountered the same problem and found a solution?

Thanks in advance...

---

### Post by Nehemiah on 2006-08-18
I think I have since encountered it switching off while the computer was on (ie: not sleeping or off).

Has no one else encountered this? Perhaps it's just my USB dongle...

---

### Post by lupine_nickt on 2006-08-18
I have the same sort of dongle, and for me it dies whenever I submit it to heavy load (e.g. lots of Bittorrent/aMule, or downloading my emails after being offline for ten days. I've got a second PC running on one, and it's been going strong with hardly any activity on it for a good month now... however, I always disable all the power management settings I can find, so that might have something to do with it.

Hopefully, once the rt2x00 driver becomes stable enough for use (it's not even close yet!), all these problems will magically disappear...

xF,

...Nick

---

