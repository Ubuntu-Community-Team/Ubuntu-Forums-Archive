---
title: "[SOLVED] dell latitude d830 not recognising wlan interface"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by muellthos on 2008-02-24
I installed gutsy server with encrypted partition on a dell d830. Accidently I switched the wlan "Kill-"
switch off. Modprobe shows the ipw3945 loaded, iwlist shows the adapter scanning, but not associated. Swithching the killswitch on only gives a message in the log. When switching the killswitch on when the notebook is off, I can see the green led light up, which according to the dell documentation  means, that the adapter is working and a wlan is found. But when I boot still noc recognisation of the interface. Also I reinstalled, still no luck. 
I installed backport modules, also no success. Tried  SMBIOS and loaded dcdbas. But I can not find any ipw3954d (regulatory daemon ???). How to get it ?. 
Is there a chance to get the iwlwifi driver working?

Thanks,

Thomas

---

### Post by muellthos on 2008-02-26
Found the iwlwifi driver iwl3945. It solved my problem quite easy. After unloading ipw3945 and loading iwl3945 the wlan came up. To make it working from boot I blacklisted ipw3945 (edit /etc/modprobe.d/blacklist and add ipw3945) and instruct modprobe to load iwl3945 (edit /etc/modules and add iwl3945). Works for me so far.

Best regards, Thomas

---

