---
title: "Prefer wireless networks over dial-up modem - In situations where this is possible!"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by daller on 2006-12-17
Hi there,

I've bought an **Option Globetrotter 3g quad** card, and set it up ([https://help.ubuntu.com/community/forum/hardware/Option3gCard](https://help.ubuntu.com/community/forum/hardware/Option3gCard))

My problem now, is that I would like to use my home wireless network instead of the modem-connection whenever possible... But if my wireless connection falls out, or I leave the network range (leaving for work, etc...) I would like it to connect through my modem.

...and the other way around, to get back onto the wireless network when I'm within the range...

The way I connect to the modem is using wvdial, so running "sudo wvdial" will connect, and a BREAK (ctrl+c, or killall wvdial) will exit.

A solution may be to have the modem stay on at all times, but this is not comfortable for several reasons. (I would like the modem to powerdown using **cardctl eject**, and the modem uses MB's on my limit even when not using it...)

Is this possible? (fiddling with route, maybe?)

TIA!

---

