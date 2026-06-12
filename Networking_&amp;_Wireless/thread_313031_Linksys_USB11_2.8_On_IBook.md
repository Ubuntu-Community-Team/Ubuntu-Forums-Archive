---
title: "Linksys USB11 2.8 On IBook"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by reuben on 2006-12-05
I'm trying to get setup with a linksys USB11 v2.8 on my Ibook (which has edgy /powerpc on it).

I see a listing in iwconfig for wlan0, and it looks alright...although it doesn't have an associated access point. I want to use this in public places, so I don't want to set it up with a specific SSID.

When I use KDE's "wireless assistant", it thinks about it for a while and then complains that I may not have turned on my wireless card. However, the power light on the USB dongle is on, and the link light is flashing green.

I read somewhere that I don't need to do ndiswrapper on this dongle, because versions prior to v4 are supported by a native linux driver. Does it sound like I need to install these?

Also, one other issue (may be unrelated) -- when I unplug the dongle and plug it back in, it seems to cause a major error. Any command that I run just freezes. However, KDE's UI is still responsive. There are no messages listed in the /var/log/messages output. Ideas on debugging this?

Thanks

---

