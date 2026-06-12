---
title: "saving default network"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by robalcorn on 2008-03-25
Hey folks my acer aspire 5102 notebook keeps logging onto another wireless network in my neighborhood whenever I boot up. And I have to keep changing it over to my routers SSid.How do I set 7.10 to log onto my network automatically from now on?

---

### Post by prshah on 2008-03-25
> **robalcorn said:**
> Hey folks my acer aspire 5102 notebook keeps logging onto another wireless network in my neighborhood whenever I boot up. And I have to keep changing it over to my routers SSid.How do I set 7.10 to log onto my network automatically from now on?

edit your /etc/network/interfaces file and add the line "wireless-essid whatever" where whatever is your router's SSID.

---

### Post by robalcorn on 2008-03-25
added your suggested line under etc/networks/interfaces and saved and rebooted but still keeps auto logging onto someone else's unsecure network.Lol though there is alot of them around... talk about free internet or what (kidding). I wouldn't do that.

---

