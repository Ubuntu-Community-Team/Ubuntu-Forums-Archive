---
title: "Madwifi-NG Ath Problem"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by BrentC on 2008-02-16
I have to set my wireless card in monitor mode. I am following the guide from Madwifi's Wiki in order to accomplish this: [http://madwifi.org/wiki/UserDocs/ChangingMode](http://madwifi.org/wiki/UserDocs/ChangingMode)

Changing the mode works, however it causes things to be a pain in the ***, royally. I have to change my WNIC to monitor mode every time I reboot and this is where the problem comes into play. By default, it shows up as ath0, which is what it should be. When I set it monitor mode via wlanconfig, it changes it to ath5, ath6, ath7, etc, or whatever athX is 1 integer higher than the last time I changed the mode to monitor. This causes a lot of problems for programs I use.

Is there anyway to fix this at all?

Thanks,
Brent

---

