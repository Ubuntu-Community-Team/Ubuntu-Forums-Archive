---
title: "Google earth crash"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by wreinders on 2009-02-09
Same for me: No Google Earth, no Compiz.
Ubuntu Intrepid Ibex, kernel 2.6.27-11-generic
Graphics card: NVidia GeForce 8500 GT
Anyone out there to help .... please?

---

### Post by chrisstewart on 2009-02-09
Hey just curious not sure if you have tried this.. I recall a similar issue where the GUI started in 640x480 and under System then Administrator and Add Hardware does it have the NVIDIA card listed?? Then I added the hardware drivers the older version installed due to age of my nvidia card and installed compiz....

Chris

---

### Post by wreinders on 2009-02-10
If I select: Administration > Hardware Drivers
I get the message : "Proprietary drivers are being used to make this computer work properly"
Two such drivers are shown:
- NVIDIA accelerated graphics driver (version 173)
- NVIDIA accelerated graphics driver (version 177) [Recommended]
none of them however is activated. If I activate either of them, my PC ends up with a broken X-windows system. The only remedy is then to use the Failsafe Terminal, and restore the original /etc/X11/xorg.conf file.

---

