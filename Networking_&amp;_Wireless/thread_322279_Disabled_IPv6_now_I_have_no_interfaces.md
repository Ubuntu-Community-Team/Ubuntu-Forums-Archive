---
title: "Disabled IPv6 now I have no interfaces"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by timmay on 2006-12-20
I followed the instructions from here [http://ubuntuforums.org/archive/index.php/t-87798.html](http://ubuntuforums.org/archive/index.php/t-87798.html) and now I've broken both Ethernet and Wi-Fi on my Dell Inspiron 6000.

Spec:-
Intel prowireless 2200bg
Broadcom BCM4401-B0 10/100 Ethernet

After changing the settings and rebooting I couldn't browse the net so I restored the config back to the original. Now I'm getting "SIOCGIFFLAGS error: No such device"

I changed these settings on another machine and it was very sucessfull and reduced the DNS lookup time from 30+ seconds to no time at all (a few ms).

Can someone help?

Thanks

---

### Post by timmay on 2006-12-20
I've now fixed this issue.

refer to my post [here]("http://ubuntuforums.org/showthread.php?p=1911881#post1911881").

---

