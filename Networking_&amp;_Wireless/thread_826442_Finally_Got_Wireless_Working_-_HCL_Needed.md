---
title: "Finally Got Wireless Working - HCL Needed"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by Guilden_NL on 2008-06-11
I had loads of problems with three laptops and one desktop that all worked with Gutsy but failed to work with Hardy.  I had purchased a Hawking card for the desktop wireless that was supposed to be supported under native drivers in Linux and it worked with Gutsy, but not Hardy. Even tried NDISWrapper etc, finally gave up.

I mentioned my move to SUSE to someone I work with and he told me that he had to move to an EDIMax card because it was a solid RAlink chipset that Hardy liked.  I bought one from NewEgg.com $30 shipped to door.  Plugged it in, and Hardy was off and running with native drivers (no NDISWrapper) in seconds. Over in SUSE, I then uninstalled NDISWrapper and the original RAlink driver for the Hawking card and WHAM! instant recognition and off and running.  Much faster than a MSFT recognition and install.

So the moral of the story is to go with one of the RAlink cards like EDIMax's that have the native Linux drivers.

Once again, I'd love to see Ubuntu maintain a native Linux driver supported HCL that users could update through moderators.  I could not find a decent HCL out on the Net that is updated.  My two cents.

---

### Post by YoungCthulhu on 2008-06-11
I had similar problems, but I had upgraded from Feisty to Hardy.  Suddenly my D-Link wireless PCI card (Atheros chipset) wouldn't work.  I finally fixed it manually but it took me about 2 weeks, me being conceptually challenged an'-all.  (My D-Link previously worked out-of-the-box since I upgraded from Dapper to Edgy)

Why did Hardy get all precious over D-Link/Atheros/MadWifi?  :confused:

Cheers

---

