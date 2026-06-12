---
title: "Atheros MadWifi Issue"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Crope on 2008-09-03
Hey guys. 

I have an Atheros 5007EG integrated card with correctly installed MadWifi drivers and I'm on Ubuntu 8.04. I can access the internet, see available networks, and the like.

I'm trying to put it into monitor mode. When I type in iwconfig, it says "No wireless extensions", and when I try to create wifi0 by typing in ```
sudo wlanconfig ath create wlandev wifi0 wlanmode monitor
``` it creates ath1 instead. If I try to destroy ath0, my computer freezes up and I have to restart.

Thanks in advance guys.. I've been giving myself a headache over this for about 3 weeks now, so any information is helpful.

---

### Post by Crope on 2008-09-04
[SIZE="1"][SIZE="1"]bump[/SIZE][/SIZE] :)

---

### Post by Crope on 2008-09-04
[SIZE="1"]Bump :\[/SIZE]

---

### Post by hawksbill on 2008-09-07
> **Crope said:**
> Hey guys. 

I have an Atheros 5007EG integrated card with correctly installed MadWifi drivers and I'm on Ubuntu 8.04. I can access the internet, see available networks, and the like.

I'm trying to put it into monitor mode. When I type in iwconfig, it says "No wireless extensions", and when I try to create wifi0 by typing in ```
sudo wlanconfig ath create wlandev wifi0 wlanmode monitor
``` it creates ath1 instead. If I try to destroy ath0, my computer freezes up and I have to restart.

Thanks in advance guys.. I've been giving myself a headache over this for about 3 weeks now, so any information is helpful.

I'm no expert here but I stumbled across your post while looking for some madwifi information.

Did you try "ifconfig ath0 down" + "ifconfig wifi0 down" before "wlanconfig ath0 destroy"

More information can be found here:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

I also found this two slots down from your original post:
[http://ubuntuforums.org/showthread.php?t=902023&highlight=madwifi+wifi0+ath0](http://ubuntuforums.org/showthread.php?t=902023&highlight=madwifi+wifi0+ath0)

hope this helps

---

