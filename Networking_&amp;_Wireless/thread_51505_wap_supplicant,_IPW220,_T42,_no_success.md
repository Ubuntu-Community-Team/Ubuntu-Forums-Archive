---
title: "wap_supplicant, IPW220, T42, no success"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by bmargulies on 2005-07-24
I've followed various guides to try to get WAP working on my wireless interface.

I have a T42 with a built-in IPW2200. It seems to be working just find with WEP.

With WAP, wap_supplicant complains, bitterly, that it never sees a WAP/RSN message from the AP. Well, when I boot XP on the Very Same Laptop, it has no problem with WAP. 

I appreciate that WAP is out there in the Universe, and perhaps the moral of the story is that it just isn't quite cooked yet.

I'm using the ipw driver that H-H installed for my by default.

---

### Post by luca_linux on 2005-07-24
You have to update the ipw2200 to the latetest version (1.0.6) since the one included in Ubuntu Hoary is oboslete (0.19).
Just follow this HowTo: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

