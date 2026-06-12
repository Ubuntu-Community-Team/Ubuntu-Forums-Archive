---
title: "Proxim wifi card using external antenna? How to tell?"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by FuzzyLogic01 on 2008-07-20
Bought an omnidirectional antenna from Radiolabs after getting a killer deal on a Proxim Gold 8480. The 8480 doesn't have the external antenna jack that the 8470 does, so I bought the connector and modded the card. Plugged the card in, and whether or not the external antenna is connected I get the same signal levels. This caused me to seriously second-guess my work on the card mod, so I bought a Proxim Gold 8470-FC. You can never have too many of these babies, right?

I am getting the same results with the 8470-FC, which has the factory external antenna jack. I know the jack is supposed to recognize when an external antenna is connected and switch to the external connection and disable the internal antenna, but can/should this be manually done in Linux? 

I'm running Gutsy on an old Dell Inspiron 8100. Honestly, though, this same problem is occurring on my HP nx9420 which is running Mandriva. I'll wipe the laptop and install 8.04 on it to further troubleshoot this issue, though. My slowly-building Linux knowledge is almost solely derived from installing distros repeatedly on hardware to learn something new. Hardly an expert here, but eager to learn. 

My guess is that I'm faced with a driver issue. If I'm looking in the right places here, it looks like the driver I am using is ath_pci. Found this using 'lshw' and double-checking with the Hardware Information applet.

Any thoughts, suggestions? I'd be willing to entertain any suggestions up to and including "Just install this distro, it'll work out of the box" but would rather avoid anything requiring new hardware (i.e. "Should have bought a XYZ-1, it works fine.") My wife will humor my purchase of two cards and an external antenna, but justifying a third card might be a little rough.

Thanks,

Fuzzy Logic

---

