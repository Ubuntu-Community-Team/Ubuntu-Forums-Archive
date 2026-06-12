---
title: "Bad WLAN performance ThinkPad T60/Intel 3945"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by guardian_de on 2008-02-11
I'm running Ubuntu 7.10 on a ThinkPad T60. I'm connecting to my WLAN via the built-in Intel 3945 network card.

As long as the wireless signal strength is good, the connection is fast. Once the connection quality drops (moving away from the access point), the achievable bandwith is cut down significantly (from > 2 MByte/s to 100 KByte/s). This would be ok if the connection would recover when I move closer to the AP, but it doesn't do so until I manually unload the driver and reload it again.

I tried both the ipw3945 and the iwl3945 driver but that didn't make a noticable difference.

Is there anyone with an idea what would help here?

---

### Post by dca on 2008-02-11
Apparently quite a bit of problems w/ this combo:
 
[http://ubuntuforums.org/showthread.php?t=569727&page=2](http://ubuntuforums.org/showthread.php?t=569727&page=2)
[http://ubuntuforums.org/showthread.php?t=602478](http://ubuntuforums.org/showthread.php?t=602478)
 
If installing and using WICD doesn't work then only other option would be to remove ipw3945 modules and install using ndiswrapper.  I don't have the parts in question but I'm very curious if anything is able to resolve it...

---

