---
title: "WMP54G V4 Signal Strength"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2007-07-31
Hey all.

I have a Linksys WMP54G V4. I did a fresh install of feisty, and the drivers work. However, when I attempt to connect to any wifi network, they all show a signal strength of 0%. Any attempt to connect to any wifi network times out. I moved my computer to 20 feet away from the router, but there was no change in signal strength.

I have also tried a WUSB54G V4, and it has the same problem. Drivers install fine, but still there is no signal strength, and any attempt to connect to a network times out. 

I have even tried both of these adapters in a different computer. I get the same problem. Is there something I am missing here?

Thanks!

---

### Post by kevdog on 2007-07-31
Read through this post -- it will give you some definite insight into the WUSB54G problem you are having.  I know at first the post will seem not relevant to you, but keep reading -- it will lead into driver installation!
[http://ubuntuforums.org/showthread.php?t=512647](http://ubuntuforums.org/showthread.php?t=512647)

---

### Post by kerryhall on 2007-08-01
Thanks! Will do! So the default drivers for WMP54G and WUSB54G are no good then?

---

### Post by kevdog on 2007-08-01
Depends what the driver is.  If you have a ra chipset and are using feisty, go with serial monkey drivers.  If using Edgy or below, to my knowledge the built-in drivers are OK.  (Not sure with Gusty yet -- Ive heard they are going to include the new serial monkey drivers as the built-in drivers, but read somewhere the other day this has not been implemented yet!)

---

### Post by kerryhall on 2007-08-01
Thanks a lot! I'll give the serial monkey drivers a try!

---

