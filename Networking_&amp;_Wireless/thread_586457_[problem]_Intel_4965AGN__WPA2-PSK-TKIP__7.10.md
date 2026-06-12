---
title: "[problem] Intel 4965AGN / WPA2-PSK-TKIP / 7.10"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by kogz on 2007-10-22
Hi,

_Configuration_ at first. It’s fresh Kubuntu **Gutsy **installation on my **Compal FL90** notebook with **Intel 4965AGN** wireless network card.

_Problem_. I can see eth0 and wlan0 interfaces in KDE network manager, I can turn them on/off and I can configure them. Unfortunately, this configuration tool supports only WEP-based wireless networks. My AP configuration: **WPA2, PSK-TKIP, no SSID broadcast**.

_Questions_:
- What is the best way to configure WPA-based wireless network under Gutsy?
- How to be 100% sure that my WiFi device is fully working, doesn’t need any drivers etc?
- Does Gutsy already have [iwlwifi](http://www.intellinuxwireless.org/) within?

Thank you very much for any suggestions,
Conrad

---

### Post by kogz on 2007-11-02
Really thx 4 help. ;]

However I solved a problem.

Generally - knetworkmanager suxx. It looks like it doesn't support WPA1/2. I've installed Wicd - and now it finally works!

---

### Post by Antman on 2007-11-03
> **kogz said:**
> Really thx 4 help. ;]

However I solved a problem.

Generally - knetworkmanager suxx. It looks like it doesn't support WPA1/2. I've installed Wicd - and now it finally works!

YEah, WICD ROCKS!! :guitar:

---

