---
title: "bcm43xx - Wireless connection dropouts"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by aaron552 on 2008-03-06
I'm running Gutsy on my Compaq V3118AU laptop. The wireless card is a Broadcom 4311.

After installing the firmware from the bcmwl5.sys file in my windows system directory (the recommended firmware, wl_apsta.o, did not work) the wireless began working fine with my WPA network at home.

But when I connect to the WPA network at uni, it seems to drop out randomly.
I might be able to reconnect normally, or i may need to rmmod and modprobe the driver (if the interface disappears) or sometimes a reboot into windows and then back into ubuntu is necessary.

Some help on tracking down this probelm would be appreciated.

---

### Post by guga31bb on 2008-03-11
hey,

i have the same problem. bcm43xx always works fine at home (or at my wife's parents house), but when i'm on the campus wireless network it drops a lot and sometimes i even need to reboot. why would it work better on some networks than others?

---

### Post by aaron552 on 2008-04-05
I've upgraded to Hardy beta and it seems to drop out a lot less. However, the range has dropped considerably and when the access point has many clients connected it will drop out. I guess it's a driver maturity issue and will get better with time

---

