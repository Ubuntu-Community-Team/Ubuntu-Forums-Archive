---
title: "Phone rings - wireless connection goes POOF!"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by garrye on 2006-09-04
New thread as I think I'm maybe looking at the wrong things as the cause of my problem.

See previous post entitled "This has me stumped!" here under "Wireless Support"

Originally thought that ACPI might have something to do with this as when power management kicks in wireless connection is lost.  This behavior is NOT seen when operating under windows.

Issue has now developed a new twist.  Bought a new three-station cordless phone with answering machine.  When this cordless phone rings, my wireless connection is lost.  Using WPA/WPA2 TKIP/AES-CCMP this happens EVERY time the phone rings.  Using WEP it has not happened yet.  I have lost the connection a couple of times but have not tied the loss to anything specific.  Therefore something in the use of wpa supplicant exacerbates the problem.

Generally as long as I am actively using the laptop, the connection remains functional.  If I leave the laptop idle, in a few minutes the connection is lost.  If I leave the laptop idle and streaming network audio, then the connection tends to hang on longer.  Occasionally it will stay connected overnight.  This has me thinking that some random event external to the laptop causes the connection loss.  Could this be a noise rejection issue?  Didn't think such things were governed by software.

Any ideas anybody?

---

### Post by NetworkGuy on 2006-09-04
Are your phones running at 2.4Ghz?   Wireless networks also run at this same band.   You can try to change the channel your wireless router works at.  (If you are at channel 1, change it to 11)  Try to get as far away as possible from your current channel and try again.  I also had problems with microwaves :)

Good luck..

---

