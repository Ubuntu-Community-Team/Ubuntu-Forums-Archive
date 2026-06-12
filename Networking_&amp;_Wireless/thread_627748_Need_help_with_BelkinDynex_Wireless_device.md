---
title: "Need help with Belkin/Dynex Wireless device"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by Thomme on 2007-11-30
O,, I bought a Dynex DX-USBG Rev. 1000 Wireless USB adapter, which is really just a Belkin FD7050 Rev. 3002 wireless device in sheep's clothing.  I had read that the Dynex devices were linux supported out of the box, the thing that I missed was that it had to be the rebranded D-link cards and not the Belkin (as the D-link Rev. B1 & C1 are Ralink chipsets that just plain work) where as the Belkin/Dynex stuff is Broadcom 4317.  Now, I know that people have gotten the broadcom Belkins working, but I think I'm running to a wierd problem.
Whenever I try to modprobe NDISWrapper it gives me a segmentation fault.  If I do it sudo or as root, it gives me the same message.  

I thought maybe I had to blacklist the older driver (I'm new to linux and it took me about 3 hours just to figure out how to do that) and it still didn't work.  Same old segmentation fault.  I can get NDISWrapper to load the driver and recognize the device, but Modprobe just won't assign WLAN0 to the card.  If anyone has any advice I would love to hear it.

Also, if you can, I'd like the advice laid out in Linux layman's terms as best as possible.  I'm pretty new to really working with linux, I've played around on it before.  I'd love so get this done so that I stop getting distracted with games in Vista while I'm doing my papers for school (Windows for play, Ubuntu for work!).

---

### Post by Thomme on 2007-12-03
I just got a differant card and it worked well (Atheros chipset), but I'd still like to see an answer to help out others with this problem.

---

### Post by divaor on 2008-01-15
I have the same problem, have you solved it yet? If not, please tell when and if you do.

---

### Post by jrelprestoo on 2008-01-20
Same.

---

