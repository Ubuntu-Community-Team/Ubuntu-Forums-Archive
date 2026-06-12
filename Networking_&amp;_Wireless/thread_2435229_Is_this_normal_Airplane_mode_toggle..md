---
title: "Is this normal? Airplane mode toggle."
date: 2020-01-17
forum: Networking &amp; Wireless
---

### Post by dalekky on 2020-01-17
Is this how the process is supposed to happen? Below is the events which occur when my laptop lid is opened and closed -

My power management settings are: Dim screen when inactive: OFF, Blank screen: NEVER, Turn off WiFi to save power:ON, Turn off Bluetooth to save power: ON, When power button pressed: Power Off

Starting from open lid with screen on and wifi/bluetooth on, this is what happens -

- close lid
- screen goes off
- WiFi and Bluetooth remains on
- open lid
- screen comes on
- Airplane mode activates, WiFi and Bluetooth turns off
- close lid
- screen goes off
- WiFi and Bluetooth remains off
- open lid
- screen comes on
- Airplane mode deactivates, Wifi and Bluetooth turns on

Is that how it's supposed to work? It seems to me that it would make more logical sense if the airplane mode activated when the screen went off and deactivated when the screen comes back on. But instead, it's toggling airplane mode on or off only when the screen activates.

This is on Ubuntu 18.04.3 LTS

---

### Post by CatKiller on 2020-01-18
> **dalekky said:**
> Is that how it's supposed to work?

No. 

Gnome got a lot less buggy after Ubuntu switched to it by default, but many of those fixes went into later releases rather than being backported. I don't know if that behaviour is one of the things that's been fixed.

---

### Post by dalekky on 2020-01-20
So is there a recommended fix for this?

---

