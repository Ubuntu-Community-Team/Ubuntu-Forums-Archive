---
title: "wireless security confusion"
date: 2020-06-28
forum: Networking &amp; Wireless
---

### Post by koleary on 2020-06-28
I have an older Linksys router named Dayton and a few days ago I changed the security mode setting from WPA Personal to WPA2 Personal.

My desktop PC is running Ubuntu 20.04.  When I checked the wifi connection it verified that I am using WPA2.

[ATTACH=CONFIG]286334[/ATTACH]

I also have an older Toshiba netbook that is running Lubuntu 20.04.  When I checked the wifi connection there it appears that I am using WPA.

[ATTACH=CONFIG]286335[/ATTACH]

Is it possible to upgrade the wifi security setting in Lubuntu to WPA2?

Thank you for your assistance.

Kevin

---

### Post by kurt18947 on 2020-06-28
I thought the Wireless Access Point - Dayton in your case - determined the wireless protocol (if that's the correct term) used by clients. I could certainly be wrong though, wait for the experts to check in on this.

---

### Post by koleary on 2020-06-29
> **kurt18947 said:**
> I thought the Wireless Access Point - Dayton in your case - determined the wireless protocol (if that's the correct term) used by clients. I could certainly be wrong though, wait for the experts to check in on this.


I also thought that the router would determine the security mode.  I'm at a loss as to why the netbook running Lubuntu says it is using WPA.  Is this even possible?

I'll also mention that my desktop PC is configured as a dual-boot machine; both Ubuntu 20.04 and Windows 10 are on it.  Not surprising, when I boot into Windows 10 the wifi connection (Dayton) is listed as "WPA2 -- Personal" there too.

Kevin

---

### Post by durexlw on 2020-06-29
> **kurt18947 said:**
> I thought the Wireless Access Point - Dayton in your case - determined the wireless protocol (if that's the correct term) used by clients. I could certainly be wrong though, wait for the experts to check in on this.

The AP defines the protocol... it would be a scary thing to define WPA2 and have someone be able to connect over WEP...

---

