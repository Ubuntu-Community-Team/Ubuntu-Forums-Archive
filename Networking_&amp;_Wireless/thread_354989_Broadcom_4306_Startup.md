---
title: "Broadcom 4306 Startup"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by HexJunkie on 2007-02-06
I followed [this]("http://ubuntuforums.org/showthread.php?t=185174") guide to get my Broadcom 4306 based card working.

It works fine, but everytime I restart the computer, I have to go into Network Manager and:

-Open the manager
-Disable the card
-Close the manager
-Open the manager
-Enable the card
-Close the manager

And then it works.

I'm hoping theres some way that I can make it automatic? Or at least a reason for why this is happening?

EDIT: It also seems to lose the connection after a few minutes. The bar stays full, and it says I'm connected, but I don't recieve packets. I have to repeat the above for it to work again.

---

### Post by ukripper on 2007-02-09
You should have tried ndiswrapper instead of fwcutter then perhaps it would be automatic. Can't comment on this as I never tried fwcutter before.

although try : blacklisting bcm43xx in Blacklist file

and reboot.

I think it is loading your previous bcmxx driver which comes with ubuntu and ignoring your new configuration while loading at startup.

---

