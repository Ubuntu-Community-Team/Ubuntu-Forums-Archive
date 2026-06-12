---
title: "HP2133 Wireless Issue"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by jurfid on 2008-09-22
I've checked a number of different paths to try to get my Broadcom 4312 working, but all to no avail.

I have concluded that the a/b/g card is in a-only mode, based on the iwconfig info:
wlan1  IEEE 802.11a  ESSID:off/any
       Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated

...and, not surprisingly, it can't see any b/g AP's.

I have not found any specific help on changing the mode of the wireless card, so I ask here for some direction.

In advance, thank you, from this Ubuntu Newbie.

---

### Post by jtappin on 2008-09-22
That rather looks like you've not got it switched on (there's a switch like the power switch but on the right hand side).

On my 2133 iwconfig reports IEEE 802.11a when the "card" has not been powered up since boot and IEEE 802.11g when it's powered up. On Ubuntu (unlike SuSE) the indicator on the switch does work. If it shows orange then you are switched off, and if it shows blue you are powered on (the blue light at least on my machine is rather fainter than the one on the power switch). You do need to hold the switch across for a second or 2 to power up the wireless (I assume this is to reduce the chance of switching it on by mistake). On reboot the wireless is always powered down.

---

### Post by jurfid on 2008-09-22
Wow!  That is incredibly frustrating!  I assumed "light on" meant powered!  Craziness!

Thanks for the reply.  Hopefully, this will allow me to get cranking on some good ol' wireless-in' later today.

jtappin, you are my new hero!

---

