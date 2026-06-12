---
title: "Broadcom 4318 64Bit Gutsy - Absolutely Stuck"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by sharpycore on 2007-12-22
Hi,
I have a Broadcom 4318 card  that I have managed to get working once before using ndiswrapper but did a clean install of the OS to try and get the bluetooth drivers working and now totally can't remember how to do it. I have searched high and low through the forums and NOTHING works. I can't find the guide that helped me do it the first time either. But Iseem to remember something about explicitly copying the windows drivers on the windows partition into a directory of the ubuntu install...

I started by trying this [http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318) but the card won't show up under ifconfig. The card works under windows so I know works. I tried installing ndiswrapper from the CD repos and then using ndiswrapper -i to install the drivers from there. No amount of blacklisting and modprobing makes a difference though.

Does anyone have a 64bit install of Gutsy with a BCM4318 card working who can just walk me through it again? I can't believe I'm this stuck considering I've managed it once before.

Thanks a lot in advance for any help.
Tom

---

### Post by sharpycore on 2007-12-25
For anyone else having this problem, please see kevdog's *excellent* thread at

[http://ubuntuforums.org/showthread.php?p=3523715#post3523715](http://ubuntuforums.org/showthread.php?p=3523715#post3523715)

And if you are looking for the 64 bit broadom drivers, impossible to find on broadcom's awful website, they are here 

[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

---

