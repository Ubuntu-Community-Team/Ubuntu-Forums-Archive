---
title: "Atheros 5212 Issue"
date: 2005-09-17
forum: Networking &amp; Wireless
---

### Post by elitegoodguy on 2005-09-17
I am running Breezy on my Toshiba P35-6111 with a builtin Atheros 5212 wireless card. I have heard ALOT of reports that ACPI didn't work very well with the Toshiba's but I figured that I would give it a try, and it works just fine.  However I am having alot of issues with the Wireless Card

When I do **iwlist scan** it comes up with my ap.
I set the correct options for Key, ap, channel, security mode, etc... but it does not see an IP.

When I do a **dhclient** the only thing that sees an IP is my wired network card.  When I have it unplugged **dhclient** just times out.  

Do I need to install the madwifi drivers? I noticed in the first step of the instructions it said to check the version of ath_hal and see if it is status 13.  Mine is a newer version and it doesn't list status 13 so it should be compatible

Any help would be appreciated

Thanks

---

### Post by elitegoodguy on 2005-09-17
Nevermind I have figured it out...  I feel stupid lol I had set it to Open mode on the router but somehow it didn't save, just switched it back to open mode now it works fine

Thanks

---

