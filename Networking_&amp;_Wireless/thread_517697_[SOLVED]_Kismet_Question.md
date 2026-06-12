---
title: "[SOLVED] Kismet Question"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Nate9009 on 2007-08-04
Hi everybody! I have a problem while running kismet that has me pretty baffled.

I managed to configure everything and got kismet itself running (score one for another Linux newb ) . But, whenever I run it 3-5 seconds (EDIT: after running Kismet a lot more I've found that the average time it stays running is around 1 minute) in my card (ipw3945) suddenly comes out of monitor mode and starts trying to reconnect to my wireless network!

The kismet UI goes haywire whenever this happens and text overlaps the normal display.

Here is the the error message:

[ Didn't detect any Cisco Discovery Packets, unlinking cisco dump Didn't see any weak encryption packets, unlinking weak file

WARNING: Sometimes cards don't always come out of monitor mode cleanly. If your card is not fully working, you may need to restart or reconfigure it for normal operation. Kismet exiting. ]

Any thoughts on what in the world may be going on? Thanks very much!

---

### Post by phefferan on 2007-08-05
I have the same problem. I am pretty sure Network-Manager needs to be shut down before kismet is launched.

---

### Post by phefferan on 2007-08-05
Okay, I've determined that if I right click on the network manager tray icon and de-select the box labaled "Enable Networking"  Kismet works flawlessly.

---

### Post by Nate9009 on 2007-08-05
Great, thanks very much, I'll try that out as soon as I can.  :)

---

