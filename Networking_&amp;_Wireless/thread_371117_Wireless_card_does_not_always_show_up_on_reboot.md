---
title: "Wireless card does not always show up on reboot"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by Chenzo on 2007-02-26
I have an hp Pavilion dv2000z with a broadcom wireless BCM4310.  I installed wireless and got it working with this tutorial:
[http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A](http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A)
However, sometimes, when I boot, knetworkmanager does not find any wireless devices, and my wireless card does not show up in system > Administration > Networking.  After a reboot or two, the wireless card will show up again and everything works.  I have searched many different howto's on the subject, but I can't seem to find anyone with the same problem.  If nothing works my only option is to reformat and use a different broadcom howto.  any suggestions would be helpful. Thanks!

---

### Post by Floppyjoe on 2007-02-26
Is it possible that sometimes your wireless interface is loaded as wlan0 and sometimes as eth1?
My laptop did not work with network manager because it always showed up as eth1 so I changed my /etc/iftab file so that the mac address of my wireless device always registers as wlan0.

---

### Post by Chenzo on 2007-02-26
I opened /etc/iftab and changed 'eth1' to 'wlan0' in front of my wireless card mac address, but I still have the same problem.  Is that the correct procedure? any other suggestions?
Thanks for the help!

---

### Post by Floppyjoe on 2007-02-26
> **Chenzo said:**
> I opened /etc/iftab and changed 'eth1' to 'wlan0' in front of my wireless card mac address, but I still have the same problem.  Is that the correct procedure? any other suggestions?
Thanks for the help!
I guess that was not the root of your problem. That was the right procedure though.

---

