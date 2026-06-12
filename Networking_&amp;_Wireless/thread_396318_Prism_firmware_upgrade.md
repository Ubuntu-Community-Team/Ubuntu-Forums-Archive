---
title: "Prism firmware upgrade"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by waster on 2007-03-29
I've tried everything to do this, but need some expert help...

I have a PCMCIA prism card with ancient firmware. I have read various instructions for upgrading it, but the limiting factor seems to be getting some kernel parameters set on compile. It looks like they ARE set in the default ubuntu config.

There are so many drivers for prism chipsets, that I've lost all control. The card works fine with orinoco and hostap. prism2_cs isn't compiled into ubuntu for some reason. 

This should upgrade the firmware:
prism2_srec -v <interface> <primary> <secondary>

but doesn't work. (It says some flags should be set on kernel compile, but they ARE set.)

Ubuntu renames the interface from wlan0 to eth1, but NOT the /proc/net/hostap/wlan0 path which the prism2_srec seems to use. Maybe if I could stop Ubuntu renaming the interface?

Any ideas appreciated. Thanks.

---

