---
title: "Losing usb wifi connection when turning on-off ext usb drive"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by domino on 2006-07-18
I have this annoying problem with losing connection to my network and usb2 stick when I power off and on my usb2 ext drive. The onyl remedy is to reboot the puter. Anyone know what's going on and how to fix this annoying problem? I'm runing dapper 6.06.


[COLOR="Red"]
solved...[/COLOR]

Apparently i needed to reinstall the driver and compile it against the 2.6.15.26-686 kernel. i haven't thoroughly tested it since it's only my second reboot on this new compile. it has not locked up. I guess we will know in the next few hour/days.

As for my problem with loosing connection with the wlan stick after turngin off my ext USB drive, my dirty sulution is to disable wlan0 from Neworking Administrator, unplug the USB stick and re-enable wlan0 again. The goog thing is it doesn't lock up the system anymore.

Thanks for everyone's reply!

---

