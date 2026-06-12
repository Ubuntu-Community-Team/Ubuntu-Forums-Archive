---
title: "how do i enable my wireless card?"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by carl19_68 on 2007-09-21
I cannot get my linksys dwl-122 to work.  in TERMINAL lshw results are as follows:


*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:88:66:fc:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.5 link=no multicast=yes wireless=IEEE 802.11-DS

---

### Post by Zorael on 2007-09-21
And if you enable through calling 'ifup wlan0' in a terminal, or through network managers in Gnome/KDE/Xfce/etc, it stays disabled?

---

### Post by carl19_68 on 2007-09-21
seems to have worked... Thanks a million!  If i run inot more problems should I tie it to this post or start a new one?

Thanks again

---

### Post by carl19_68 on 2007-09-21
seems to have worked... Thanks a million!  If i run inot more problems should I tie it to this post or start a new one?

Thanks again

---

### Post by HokeyFry on 2007-09-21
i would continue to tie it to this post and just dont mark the thread as solved

good luck and godspeed

---

