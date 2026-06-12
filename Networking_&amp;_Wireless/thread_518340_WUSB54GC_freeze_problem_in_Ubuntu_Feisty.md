---
title: "WUSB54GC freeze problem in Ubuntu Feisty"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by Rollinpizza on 2007-08-05
Hi people, I bought a wireless usb adapter 2 days ago. This adapter is the Linksys WUSB54GC. I followed the following howtos to install it:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=wusb54gc](http://ubuntuforums.org/showthread.php?t=400236&highlight=wusb54gc)

[http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc](http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc)

Thanks to them, I got to work the adapter in my ubuntu feisty ^^. However, I have a little problem and it is the same problem that explains in this post:

[http://ubuntuforums.org/showthread.php?t=382498](http://ubuntuforums.org/showthread.php?t=382498)

My ubuntu feisty is an upgrade from edgy that is the version system which I had before.

Do u know what is the solution? Is it a driver known problem? Anybody has the same problem?

Thanks for your help!!! ;)

---

### Post by Rollinpizza on 2007-10-30
With Ubuntu Gutsy, the problem has solved but ubuntu uses a serialmonkey driver called ralink 2x00. This drivers is a little unstable with this linksys model (blocking all usb ports and random disconnections). Maybe in new releases, it solves the problem. Meanwhile, it works like a charm using ndiswrapper. ;)

Regards!

---

### Post by MariusSilverwolf on 2007-10-30
It's written for Gutsy, but *should* work for Feisty if you adjust lib, mod, and source packages accordingly:  [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

Not the EXACT same model as what you're using, but they use the same base chipset, last I checked.

---

### Post by Rollinpizza on 2007-10-30
Thanks for the help but the chipset of WUSB54GC is RT73 :( . In feisty, I tried with rt73usb driver of serialmonkeys and it worked but sometimes there was random disconnections or my usb ports didn't work.
Anyway, with ndiswrapper works very well. ^^

---

