---
title: "Ubuntu 9.04 Wireless question"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by DODGEIT105 on 2009-04-24
Does Ubuntu 9.04 have support for the Atheros AR5007 802.11 b/g Wifi Adapter? 8.04 and 8.10 did not.

---

### Post by Rocket2DMn on 2009-04-24
I see two bug reports open right now: [lpbug]316795[/lpbug], [lpbug]339330[/lpbug]
They complain about problems with this card, so I would guess that the problems are not fixed yet.  One mentioned that in Intrepid they could blacklist the ath_pci module and use this card, it's possible that this will work in Jaunty as well.
Here is a key passage from the first bug:
> It seems mostly solved, BUT...users still need to disable the wireless in Hardware Drivers to override the ath_pci module which takes over where ath5k should be in place, I would suggest that if possible disable BOTH at bootup and let the user choose which to use, although this point doesn't seem to have been raised yet, but would solve the problem with newer HP/Compaq laptops not being able to boot correctly due to ath_pci interfering with the kernel on boot - ref bug 287244.

Also...once its working, as in Intrepid the connection is **very** dodgy...i.e. keeps cutting out intermittently at random intervals ref bug 315438 which was reported separately by me as I thought it might be 2 separate issues causing it, but it only seems to be when there is high bandwidth usage...could also be that I just don't notice the cutout with simple web browsing - I am with O2 for broadband in the UK with DSL2Max which maintains the high bandwidth regardless of network congestion....it is a 1 to 1 contention ratio, so constant high bandwidth is guaranteed, it isn't the router/line as it works fine in Vista.

It seems that it is a bit of a pain, but the problem can be worked around in Jaunty.

---

### Post by JoshuaRL on 2009-04-24
> **DODGEIT105 said:**
> Does Ubuntu 9.04 have support for the Atheros AR5007 802.11 b/g Wifi Adapter? 8.04 and 8.10 did not.

[http://ubuntuforums.org/showthread.php?t=1132608\](http://ubuntuforums.org/showthread.php?t=1132608\)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1120050](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1120050)
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

From those links, it looks like it will.  But you'll either have to use the ath5k or madwifi driver.  Or maybe ndiswrapper.  But it seems like it will require some testing and a little bit of work.

---

