---
title: "Network adapter driver question"
date: 2005-06-18
forum: Networking &amp; Wireless
---

### Post by RubberChipmunk on 2005-06-18
I was using winblows for years before even learning that Linux existed. Finally made the switch, but I'm having problems with the driver for my wireless network adapter.

Ready for this? I'm using a NetGear wg311v2. Yes, that's right, the one with the TI acx111 Chipset. It shall henceforth be known as *wlan0* Ubuntu, when I installed it, provided the experimental open source acx100/acx111 driver. The driver provided was the acx100-0.2.0pre8. This version does not provide support for WEP encryption. I've tried the ndiswrapper workaround, but it did not work. At all. So, I began researching this open source driver, and found that there is a new version of the driver (er... a revision of this version) with support for WEP, acx100-0.2.0pre8_plus_fixes_57 (51 was when WEP was first available).

I found a tutorial on how to replace the driver, and I followed every step to set it up. However, when I removed the preexisting driver, it apparently didn't really go away. For some reason, after I removed it, i did an **iwconfig** which revealed that wlan0 was still active. It should not have been there.

Now, when I execute the new driver's activation script, it does not work because it cannot overwrite the preexisting wlan0.

How can I remove wlan0 from my system and fully remove the old driver so that I can install and set up this new one?

---

### Post by RubberChipmunk on 2005-06-18
I accidentally posted this in the Warty forum. Can a moderator please move this to Hoary? Thanks.

---

