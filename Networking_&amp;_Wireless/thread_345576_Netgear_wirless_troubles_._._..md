---
title: "Netgear wirless troubles . . ."
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by seanbecker on 2007-01-24
I have seen several posts about this specific Netgear WG311v3 card, running on Marvells chipset.  However none that I have seen have been able to help me.  I am not sure if my problem lies in the drivers that I am using or Ndiswrapper.  Basically once I install Ndiswrapper -utils, and attempt to install my drivers (which I downloaded off the internet) mrv8335x.inf and mrv8335xp.sys, the ".inf" file takes (driver installed hardware present), but the ".sys" file does not and ndiswrapper -l displays 


mrv8335x driver present, hardware present
mrv8335xp.sys invalid driver!

I have also tried it with the drivers Netgear, supplied both on their cd and their website, and used both XP as well as Win2000 Drivers (WG311v3.inf, WG311v3xp.sys, and also tried WG311v3NT.sys).  The INF files always load correctly (driver present, hardware present) but the .sys files NEVER do.

So logically I thought maybe my Ndiswrapper just needs to be updated, performed uninstall via make uninstall, followed directions off of another post, as well as ndiswrappers wiki.  Reinstalled using ndiswrapper-1.34.tar.gz package.  Still got same error.

I am not sure where my problem lies I used this Ndiswrapper package and marvell drivers on Slackware 11.0, using the same machine and card just a week ago.  And it worked correctly.

Please help if you have any ideas.

This is Ubuntu 6.10 edgy, dual boot with XP, 2.8Ghz p4 proc, 1 gig ram.

---

