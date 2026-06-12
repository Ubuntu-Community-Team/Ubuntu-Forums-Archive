---
title: "Toshiba Satellite A500 02F"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Northern Mike on 2009-11-21
PSAR3C-02F008
Loading for a friend who liked Ubuntu 9.1 on my Dell.

Karmic Koala 32 bit

Issues: No 3d video effects. 512 mb NVIDIA GeForce G 210M, tried the ubuntu recommended 185 Nvidia driver, unreadable garble, reloaded 9.04 and tried the same 185 driver, same.  Reloaded 9.1, tried NVidia 190.42 driver, still no good, system fans stays on, major system hangs, screen borderline unreadable.  Reloaded 9.1 again and left the driver out, everything works fine just no 3d support so we can wait for a proper driver.

No wireless:   Realtek 802.11 bgn, not sure which card.

Suggestions?

---

### Post by Northern Mike on 2009-11-21
Ok its a RTL8191SE wireless card.  I read on another thread to email Realtek and they will send you a driver.  Tried that we'll see if they respond.  On a side note I pulled my intel 5100 card out of my other machine an tried it.  It worked fine but without antennas to connect to it it has a very short range and I don't want to buy another card.

---

### Post by Northern Mike on 2009-11-22
Threw in a different HD and tried again so as not to corrupt my current load, added the Nvidia 190.42 driver from these instructions.

[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

However there are still issues for this card, static lines, black patches, very slow etc.  Makes me log in each time.   Don't install this driver yet.

---

### Post by Northern Mike on 2009-12-05
Well still no sucess with the 3d effects, do not use that driver.

However Realtec replied quickly with their rtl8192se_linux_2.6.0010.1116.2009.tar.gz driver.   It now has wireless and is back with its owner and we can wait for Nvidia to make a good driver.

---

### Post by Northern Mike on 2009-12-05
Also no keyboard back light.

---

### Post by asiandub on 2009-12-30
There's a new NVIDIA driver (190.53) out... Still no 3D support, at least as far as I could find out...

Cheers,
Jan

---

### Post by Northern Mike on 2010-01-10
Yes I really wish I had suggested a Dell instead of a Toshiba now.

---

### Post by Northern Mike on 2010-01-10
Nvidia has removed the G210M listing as being supported by any of the drivers.   But reading the Nvidia forum it sounds like it is being worked on.  Hopefully soon, seems the G210M is in a lot of machines now.

---

### Post by Northern Mike on 2010-12-02
All working well now under 10.04

Thank you developers.

---

