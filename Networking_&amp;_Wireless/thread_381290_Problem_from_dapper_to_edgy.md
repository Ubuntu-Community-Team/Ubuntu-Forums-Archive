---
title: "Problem from dapper to edgy"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by awperk on 2007-03-10
I'm have a problem with a prism 2.5 chipset wireless card. It worked on startup when i originally installed dapper but when i just updated to edgy, everything went haywire. The card's id was eth1 on dapper and now for some reason is wlan0 and says it's just an ethernet connection instead of wireless. I also can't seem to enable the card on edgy. My cards old profile is still listed under /etc/network/interfaces with the correct settings. Is there anyway to switch back to the old eth1 or change the wlan0 to identify my card correctly. thanks.

---

### Post by Floppyjoe on 2007-03-11
> **awperk said:**
> I'm have a problem with a prism 2.5 chipset wireless card. It worked on startup when i originally installed dapper but when i just updated to edgy, everything went haywire. The card's id was eth1 on dapper and now for some reason is wlan0 and says it's just an ethernet connection instead of wireless. I also can't seem to enable the card on edgy. My cards old profile is still listed under /etc/network/interfaces with the correct settings. Is there anyway to switch back to the old eth1 or change the wlan0 to identify my card correctly. thanks.

Maybe you just need to move the properties of your eth1 interface to the wlan0 interface in the file /etc/network/interfaces.

---

### Post by awperk on 2007-03-13
i tried to alter the contents of the interfaces file but it is restricted to saving.

---

