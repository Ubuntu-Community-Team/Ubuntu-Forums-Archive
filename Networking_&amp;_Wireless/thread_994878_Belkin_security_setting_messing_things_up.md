---
title: "Belkin security setting messing things up"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Alain65 on 2008-11-27
Hi,

I'm using Ubuntu 8.04 and after a night of messing around I finally got the wireless router to work (Belkin F5D8233-4 with usb adapter). I used ndiswrapper.

The initial problem was largely solved by putting the adapter at a different location, yet that doesn't work anymore. The computer is about 7 meters away from the router.

This morning I set the security (through the webpage) at WEP hex, as in my Network Settings. At that point the wireless icon on the router died on my.
I tried disabling the security. When I reboot the router, the icon starts up again, but then the light of the adapter stays blue - no blinking.

Anyone know of a possible solution?

Thanks,

Alain

---

### Post by Alain65 on 2008-11-27
Hi,

Problem solved.
After reboot, restart the network ( /etc/init.d/networking restart ).

Alain

---

