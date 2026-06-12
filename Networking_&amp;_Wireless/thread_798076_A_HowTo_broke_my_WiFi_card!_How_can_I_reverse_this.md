---
title: "A HowTo broke my WiFi card! How can I reverse this?"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by germclown on 2008-05-17
Hi...

I recently bought an ASUS WiFi card (AirForce1) but it wouldn't work OoTB anymore in Hardy (it did in Gutsy). I used this guide:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

which was the only way I found to get it to work, but I noticed that it ran slowly (30kB/s max; normally 180ish in XP). I thought "okay, better something than nothing" but when I went back to XP, the speed was slow there as well! I can't even play EVE properly anymore because the connection is slow and the game keeps dropping the connection. My Laptop's USB WiFi works fine on both computers (in both OSs); it's probably this card. Pings are fast with the ASUS card, though occasionally dropped (maybe 5%).

So, Question:

Is the procedure reversible? Can I revert to the old firmware through Ubuntu? I can't find anything useful online (only firmware for Asus routers). I'd hate to think I've essentially bricked my card...

Please help? (and thanks)

---

### Post by Ayuthia on 2008-05-17
> **germclown said:**
> Hi...

I recently bought an ASUS WiFi card (AirForce1) but it wouldn't work OoTB anymore in Hardy (it did in Gutsy). I used this guide:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

which was the only way I found to get it to work, but I noticed that it ran slowly (30kB/s max; normally 180ish in XP). I thought "okay, better something than nothing" but when I went back to XP, the speed was slow there as well! I can't even play EVE properly anymore because the connection is slow and the game keeps dropping the connection. My Laptop's USB WiFi works fine on both computers (in both OSs); it's probably this card. Pings are fast with the ASUS card, though occasionally dropped (maybe 5%).

So, Question:

Is the procedure reversible? Can I revert to the old firmware through Ubuntu? I can't find anything useful online (only firmware for Asus routers). I'd hate to think I've essentially bricked my card...

Please help? (and thanks)

Well, the drivers that you are using in Ubuntu should not affect how XP works.  It only translates things for the operating system to handle.  It does not go and update the firmware in your wireless card.  My laptop is currently multi-booting Vista, Gentoo, Arch, and Ubuntu and they have different drivers running (Vista driver, NDISwrapper, and b43) and they all run differently.

If you have a wired connection, you might try it out to see if something else is running slower or maybe trying a different channel on your router.  There could be some interference in the channel.

---

