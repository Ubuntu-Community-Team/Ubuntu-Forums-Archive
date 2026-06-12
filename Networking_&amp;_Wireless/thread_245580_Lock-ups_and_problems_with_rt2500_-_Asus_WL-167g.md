---
title: "Lock-ups and problems with rt2500 - Asus WL-167g"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by Jimmy The Clown on 2006-08-28
Alright banging my head against the wall, so it's time to ask for help.

Basically I bought an Asus WL-167g because it uses the open source ralink drivers. I used it on my old desktop in Dapper with no problem - plug and play and everything works all sexy like. However, I inherited a newer computer that I intend to turn into a mythbox and no matter what I do this thing locks up when trying to get wireless going. As soon as I enable the device in the networking dialog it pops up with the "enabling device" progress bar and then goes full lock. No keyboard, no mouse, no numlock, etc.

I've done my research and tried the nightly build of the rt2500 driver with no luck. I have tried using network manager but it won't connect to any networks (presumably because the card is not enabled). I have tried on both the latest 386 and 686 kernels with no luck. Someone suggested I try the server kernel, but I haven't done that yet.

Apparently there is some malfunction between the rt2500 drivers and SMP kernels, but I do not know for sure that this is my problem. Lately I have also begun to question whether the rt2500 is being used. According to iwconfig it is using rt2500usb and I know that most usb devices use the rt2570 driver. Is rt2500usb really just another name for rt2570??? Will building the latest rt2570 or even the rt2x00 experimental help my situation?

Anyone out there have this problem and get it licked? Honestly I spent less time getting my Broadcom card going on my laptop with ndiswrapper...


-JTC

---

### Post by Jimmy The Clown on 2006-08-30
Switched to the server version of the latest kernel and am no longer having problems. This confirms that the issue is with PREEMP and SMP enabled kernels. Using this kernel is merely a short term fix. The best fix would be recompliling a new 686 kernel without PREEMP or waiting for the rt2x00 drivers to stabilize and install easily. Hope this helps someone.

-JTC

---

### Post by Endow on 2006-08-30
I'm in dire need of a wifi adapter.But my prob is Ubuntu out of the box compatibility (beeing a newbie as far as probilem solving is concerned).Would you consider this wifi adapter in particular a good purchase for someone who plans on using it (Dapper Drake 32bit) right away??

If not have you any other USB suggestions?:confused:

---

### Post by Jimmy The Clown on 2006-08-30
Horrible choice for out of the box compliance as are all the rt2500 chipsets. Should be great since it is the best open source driver for wifi, however Ubuntu dropped the ball on this and included a driver that is incompatible with any of the standard kernels. I've spent probably a good 8 hours trying to get this thing working and have only come up with a partial fix. Great out of box choice for just about any distro but ubuntu unfortunately...

-JTC

---

