---
title: "wifi card stops working after power cord is unplugged temporarily"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by joseelsegundo on 2005-05-17
jeez, then don't unplug it :)

I am setting up a headless server and I want to use wireless so I don't have to run CAT5 through my very hot attic.  I have set up a rtl8180 based wireless NIC using nsidwrapper and it works great, until I unplug everything and move the box to its new location and plug the power back in.  When I boot it up I get a couple flashes from the activity light when it modprobes ndiswrapper, but nothing after that.

dmesg shows it finds everything ok:
```
wlan0: ndiswrapper ethernet device 00:50:fc:f1:42:ce using driver net8180
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
ndiswrapper: driver net8180 (Realtek,10/07/2004,5.173.1007.2004) added
```

To get it to work again i have to uninstall everything and start again from scratch which is starting to look worse than running CAT5. :)

I'm guessing that there's some sort of ACPI evilness going on here.

Any ideas?

---

