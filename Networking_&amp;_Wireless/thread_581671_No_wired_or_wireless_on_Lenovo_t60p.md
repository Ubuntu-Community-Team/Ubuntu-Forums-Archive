---
title: "No wired or wireless on Lenovo t60p"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by mlilien on 2007-10-19
So, I installed Gutsy last night with the alternate install cd (I tried first with the live cd, but it didn't seem to work).  And now I can't get wired or wireless internet.

By default, it's trying to use ath0:avahi, but it says that something's missing in /proc/net/something.

And it won't recognize my wireless card either.  This was also the case in Feisty, but I solved it with madwifi, using the instructions here [http://forum.thinkpads.com/viewtopic.php?t=43159&highlight=](http://forum.thinkpads.com/viewtopic.php?t=43159&highlight=).  I downloaded both those files onto a thumbdrive and brought them into Gutsy, but I can't untar the madwifi file.  I downloaded the latest release from madwifi.org, but got a number of errors when trying to make it.

The wireless card is an Intel Pro 3945ABG, if that helps at all.

Also, for some reason, I can't select any resolutions that are widescreen.  It only gives me options for 4:3 resolutions.  If you know how I can fix that, I'd also appreciate it.

Thanks for the help

---

### Post by mlilien on 2007-10-21
So, I was told that I shouldn't need madwifi for Gutsy, that I should be able to use the restricted drivers manager.  However, I only see the ATI driver in my restricted drivers manager.

What do I need to do to get the drivers for ipw3845?

---

