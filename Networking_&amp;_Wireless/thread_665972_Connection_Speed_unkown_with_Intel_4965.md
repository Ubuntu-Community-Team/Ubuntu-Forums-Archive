---
title: "Connection Speed unkown with Intel 4965"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by eteq on 2008-01-12
I have a brand new Asus F8Sv-B1 laptop, and I'm having a small annoying issue with the wireless under Gutsy.  The iwlwifi driver included in Gutsy worked, but with some issues (various random disconnects, slow connection, etc), so I manually installed the latest iwlwifi drivers.  It now works beautifully, except for one thing: When I go into the "connection information" dialog in roaming mode, the speed is listed as "Unknown".  In the same fashion, if I look in the network tools control panel, the wlan0 connection is listed as "Link speed: not available".  Does anyone know if there is a solution to this?  Mainly I just want to know when I'm in 802.11g mode, and when I'm in 802.11n .  I imagine this could be an issue with the iwlwifi drivers (as they are still in very active development), but I want to make sure it isn't a known problem with other Ubuntu setups...

---

### Post by Helper_Monkey on 2008-01-14
I have the same problem with my 4965. If I put my router in N-only mode, I cannot connect. I think I saw something on the forums that said that the linux drivers cannot connect at N rates. Can anyone point to some actual documentation about this?

---

### Post by eteq on 2008-01-16
I'm not certain, but I *think* I was able to connect to a router in n-only mode (I'm not certain it was in n-only, that is)... but I was unable to confirm, as I still can't see the link speed...

---

### Post by Kyle138 on 2008-03-02
Mine definitely connects 802.11g mode in gutsy. My wireless router lists which mode clients connect to it as. Sure enough mode g when I boot in gutsy, and mode gn when I boot windows. It'd be nice if the iwlwifi drivers reported this, or if they connected in n mode for that matter.

---

