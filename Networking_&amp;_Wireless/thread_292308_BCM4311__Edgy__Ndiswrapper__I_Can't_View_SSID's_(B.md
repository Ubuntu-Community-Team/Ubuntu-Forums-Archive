---
title: "BCM4311 / Edgy / Ndiswrapper : I Can't View SSID's (But I Can Connect To Them)"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by odelay on 2006-11-03
I hate to start another thread about the BCM4311 chip (using ndiswrapper) & Edgy, but I couldn't find another thread addressing just this issue, and I don't want to hijack someone's thread.

After the Edgy update, ndiswrapper & the wireless driver were unaffected and still working (yay!).  However, when I go to System>Admin>Networking and go to configure wlan0, I'm no longer able to view the broadcast signals (SSID's).  Luckily, I am able to connect to a network fine by manually entering the SSID (i.e. "linksys").  When I click the pull-down tab that used to give me a list of all the SSID's, nothing shows up.

I've reinstalled ndiswrapper and everything with no real change.

So technically I can still use my wireless assuming I know the name of a nearby SSID.  Has anyone else had this problem?

---

### Post by fie on 2006-11-16
I'm having the same problem with the Intel Corporation PRO/Wireless 3945ABG. I installed kwavecontrol and It's able to pick up networks if it runs with root perms. But when I use that to detect/connect I have problems with DHCP. This wouldn't be a problem if I only used my laptop at my house, I could just enter my ssid. Anyway, if anyone else has an idea I would appreciate it.

---

### Post by odelay on 2006-11-16
I still haven't found an official solution...but in the meantime I use a program called "wifi-radar" (search for it in Synaptic) to view local connections and their signal strength with a GUI.

---

