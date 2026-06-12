---
title: "Ndiswrapper still needed for Hardy?  Wireless works no questions asked!?"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-07-11
I recently changed from Gutsy to Hardy and they have made changes in the wireless.  

I have an Intel card and I remember in gutsy setting up ndiswrapper to get wireless to work.  Then I had to get wpasupplicant.

Hardy, however, was able to use my wireless connection, albeit unsecured, during the alternate install. 

I actually installed hardy twice.  The first time I, by default/habbit, went and installed naiswrapper and windows drivers and had all kinds of problems with netowrkmanager and wap.

The second time I installed hardy I did nothing with ndiswrapper.
I just activated roaming mode, my network was found as a WPA2 network and all is well.

Is ndiswrapper still needed?  I even purged ndiswrapper just to see if it was there.  It's not.

---

### Post by netztier on 2008-07-11
> **Mysticle31 said:**
> 
Is ndiswrapper still needed?  I even purged ndiswrapper just to see if it was there.  It's not.

Obviously, you've fallen lucky with your WLAN NIC and the drivers provided by Hardy's newer Linux kernel. No, you won't be needing ndiswrapper anymore on that machine. :-)

Ndiswrapper is just a kludge to use Windows NIC drivers with Linux - once the kernel supports the NIC directly, the need for ndiswrapper falls away.

regards

Marc

---

### Post by trendless on 2008-07-12
Check the connection speed tho'; I was happy to be able to use the bc43xx drivers in Hardy, but it is only capable of 11Mbps; Ndiswrapper is still the only way I'm aware of to enable 54Mbps connectivity... which is the only surefire way of streaming video without choppiness over WLAN.

---

