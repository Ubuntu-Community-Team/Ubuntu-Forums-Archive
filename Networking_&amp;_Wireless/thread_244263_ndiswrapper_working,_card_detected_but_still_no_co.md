---
title: "ndiswrapper working, card detected but still no connection?"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by Cubiq on 2006-08-26
Don't know if I'm reinventing the wheel here, but maybe I can save few hours of sleep to someone.

- if your ndiswrapper detects your card
- iwconfig shows up ethx correctly
- (maybe) even the access point seems to be found
- and there's no logical reason why it souldn't work

... prabably it's your AccessPoint falt. Wire connect to your router/AP and:

- TURN ON SSID broadcasting (!!)
- remove any "speed burst" capabilities many APs these days have (eg: 108mbps, frame burst, 125mbps, etc...)
- uncheck 54g Protection (or .11g protection)

I was going to give up when finally I tried the aboves and the wireless connection magically came up! WPA-TKIP is also working through wpa-supplicant. 


PS: I have a Belkin BCM4318 PCI wireless adapter.

---

