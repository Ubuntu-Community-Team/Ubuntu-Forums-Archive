---
title: "WPA not verifying"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by FIONEX on 2007-03-03
Hey guys

I just upgraded IEEE80211, IPW2200, and IPW2200 firmware.  I'm trying to connect to my network, using network-manager, when WPA is enabled, but after I type in my password, it doesn't connect.  So I disabled WPA from my router and tried to connect, and it's all good.  The funny thing is, I had WPA working before the upgrade.  Any ideas on what it might be? 

If you need lsmod data or autoconf.h date, I will post them.

---

### Post by Mr. C. on 2007-03-04
If SSID broadcast is disabled, try enabling it, connecting w/WPA, and then when all works, disable SSID broadcast if you desire.

MrC

---

### Post by FIONEX on 2007-03-04
SSID is enabled.  If I configure my router to not use WPA, everything is good, but if WPA is enabled on the router, i can't connect to it with my laptop in linux (but ofcourse windows works).

---

### Post by FIONEX on 2007-03-04
Actually I figured something out, but I dont know how to work it.  It turns out there's a patch for IEEE80211.  [http://ieee80211.sourceforge.net/#patches](http://ieee80211.sourceforge.net/#patches) and the first one on there is my problem (dmseg shows "michael_mix: tfm_michael == null").  The problem is, I HAVE NO IDEA how to apply this patch.  when I try to "sh" it, it gives me an error.  Any ideas?

---

### Post by Mr. C. on 2007-03-04
Sorry my suggestion wasn't helpful in this case.

I know nothing about said patches.  Sorry.

Best of luck,
MrC

---

### Post by Mr. C. on 2007-03-04
Sorry my suggestion wasn't helpful in this case.

I know nothing about said patches.  Sorry.

Edit: I should have been more clear.  I kjnow nothing about the intent of those patches.  How to apply them is trivial.

The patches can be applied using the "patch" utility (apt-get patch).  You use it like

$ patch < patchfile 

from the proper directory.  You may need to provide a -p0, or -p1 option if patch complains that it can't find the file.

Best of luck,
MrC

---

