---
title: "reboot/shutdown hangs at &quot;Reconfiguring Network Interface...&quot;"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by domino on 2006-07-22
I have this annoying problem when I reboot everything is going fine until I get to a point when it just hangs at "Reconfiguring Network Interface...". Is there any logs I can look at to see where the problem is? Maybe a configuration setting not correct?

- onboard 10/100 NIC (never used/disabled)
- USB2 802.11g USB stick (static IP)

Any help is appreciated.

[COLOR="Red"]
solved...[/COLOR]

Apparently i needed to reinstall the driver and compile it against the 2.6.15.26-686 kernel. i haven't thoroughly tested it since it's only my second reboot on this new compile. it has not locked up. I guess we will know in the next few hour/days.

As for my problem with loosing connection with the wlan stick after turngin off my ext USB drive, my dirty sulution is to disable wlan0 from Neworking Administrator, unplug the USB stick and re-enable wlan0 again. The goog thing is it doesn't lock up the system anymore.

---

