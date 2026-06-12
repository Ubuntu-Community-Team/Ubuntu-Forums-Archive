---
title: "BCM4313 wpa2(aes)-connection failed - sta-driver"
date: 2013-09-18
forum: Networking &amp; Wireless
---

### Post by Eike_Schwarzwald on 2013-09-18
Hi guys,

I use Ubuntu 13.04 on my Lenovo TP-E335 and i'm having a really weired problem with the wifi-adapter.
It's a Broadcom BCM4313. 

There are two drivers available, the proprietary bradcom-sta(wl) driver and the open-source brcmsmac driver.
They both have some bugs, the brcmsmac causes extremely high power consumption and the signal quality is so bad that the connection already fails at 10 meters distance from the access point. The wl driver doesn't have that problem, so I chose this one. 

BUT now the problem:
The wl driver can't connect to any wpa2/aes/ccmp secured network. As I try to connect to it via NetworkManager, it keeps on prompting the passphrase window.
WEP, WPA/TKIP and unsecured networks work perfectly.
My current workaround is to change the encryption to WPA1 on every network I have access to, but I really don't like that method. 

Can you help me? 
Thank you in advance! :)

Eike 
ee

---

### Post by forkandles on 2013-09-18
Is this thread of any help?

[http://ubuntuforums.org/showthread.php?t=2174901&p=12791184](http://ubuntuforums.org/showthread.php?t=2174901&p=12791184)

---

