---
title: "[SOLVED] Linksys WPC54g 2.0 PCI Problem..."
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by TenPlus1 on 2008-01-06
For some reason, Ubuntu 7.04 worked perfectly with my Linksys WPC54g 2.0 PCI card and let me share my internet connection and files with my wifes laptop...

Ubuntu 7.10 on the other hand finds the card, allows me to configure but the blasted thing wont work at all and I cannot figure out why...

Any ideas ???  Have tried the Ndiswrapper route with no luck either... need idiot proof instructions I think...

---

### Post by TenPlus1 on 2008-01-08
Good news, I managed to sort out this wireless niggle...  Turns out the drivers they recommended for the Linksys WPC54g v2.0 dont actually work.. but.. the v4.0 driver worked perfectly in ndiswrapper (attached)...

---

### Post by rustybronco on 2008-01-08
Odd, works fine natively for me.  
[http://ubuntuhcl.org/pub/reviews.php?product_id=408](http://ubuntuhcl.org/pub/reviews.php?product_id=408)
was it an upgrade from 7.04 to 7.10 or a fresh install?, fire up a live cd then plug in the card and try it that way.

---

