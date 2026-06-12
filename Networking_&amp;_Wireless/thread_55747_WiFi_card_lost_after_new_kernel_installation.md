---
title: "WiFi card lost after new kernel installation"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by xav_38 on 2005-08-10
Hi,

In order to enable DRI for my video card, I had to recompile my kernel (hoary 5.04). 
I thought I used the original config file, then I changed to processor type and recompile the kernel.

Once installed and rebooted I finally got the driver enable (glxinfo shows that direct is enabled) but I realized that my wlan0 can't be activated anylonger (it says no card present) while it was running greatly under the original kernel.

I have an omnibook 6000 with a DLink pcmcia wireless 802.11b.

any idea to enable the wifi card ?

regards
Xavier.

---

### Post by firecat53 on 2005-08-11
Perhaps you  need to download the driver source and recompile it as well?

The madwifi drivers in the repository didn't work for my card. I had to get the source for the newest version and compile it. And then compile it again when I upgraded kernels!

---

### Post by xav_38 on 2005-08-11
Why should I install a new driver while the existing driver was already working before I recompile the kernel ?

---

### Post by firecat53 on 2005-08-11
Sorry, I can't answer that definitively for you! I'm new at this too! I'm just telling you what worked for me! It's actually very easy to recompile...there's a good how-to on the forums here (for a different wireless card, but the idea's the same).

Scott

---

