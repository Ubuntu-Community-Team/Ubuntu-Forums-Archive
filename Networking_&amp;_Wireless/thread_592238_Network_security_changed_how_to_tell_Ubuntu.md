---
title: "Network security changed: how to tell Ubuntu"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by KillerSponge on 2007-10-26
Hi,

I've recently changed the security of my WLAN from WPA2 to WEP (because of an XP SP1 machine that couldn't handle WPA2). Now Ubuntu constantly tries to connect to the WLAN with WPA2, which (of course) doesn't work. I constantly have to set it manually, and when I am at a different location, set it to free roaming mode again. Is there any way to change the way Ubuntu automatically connects to a WLAN?

Thanks :)

---

### Post by Steve1961 on 2007-10-26
Applications-System Tools-Configuration editor

then

/system/networking/wireless/networks/

Select the network name and in the right-pane delete the key

When you try and reconnect network manager will ask for the new key

---

### Post by KillerSponge on 2007-10-26
Thanks, I didn't know about that tool! :)

---

### Post by Steve1961 on 2007-10-26
Glad it helped

---

