---
title: "[SOLVED] Wlanconfig missing"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by gary22 on 2008-09-06
I have tried to run wlanconif numerous times and it has failed. It comes with the message no such program. This is the first time I have fired up the program since I installed it. So fare the rest is working

Thanks
Gary22

---

### Post by spd106 on 2008-09-06
If you are referring to the iwconfig command then it should be present on a default install of all versions of Ubuntu as it's in the Wireless-tools package.

If you're referring to the wlanconfig tool that's used by the [madwifi]("http://madwifi.org/") driver then you will have to install the madwifi-tools package from the universe repository.

---

