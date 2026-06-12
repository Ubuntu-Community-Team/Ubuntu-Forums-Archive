---
title: "Wireless Networking manual enabling"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by rosarioarun on 2008-07-05
Most of the time when i boot my hardy, my wireless lan is not enable(Even though if the wlan switch is on). I have to restart again to get it enabled.  If i boot my hardy with the switch off also same case. 
I mean, when i go to network manager no Wlan option at all.

If there any command to mannually enable the wlan. I mean can i enable the wlan after switching it on after boot time.... What is the procedure for it.

---

### Post by df6269 on 2008-07-05
You can use ifup command to enable your wlan.
example:
#ifup ath0 
or
#ifconfig ath0 up

---

