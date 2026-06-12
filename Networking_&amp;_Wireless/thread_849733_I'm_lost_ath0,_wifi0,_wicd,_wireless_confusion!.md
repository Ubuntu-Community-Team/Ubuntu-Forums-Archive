---
title: "I'm lost: ath0, wifi0, wicd, wireless confusion!"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by quixote on 2008-07-04
I have wireless working thanks to [wieman01's excellent howto]("http://ubuntuforums.org/showthread.php?t=318539"), but it would be nice for many reasons to have a GUI wireless manager running.

I'm using Hardy, have an Atheros 5212 chip, use WPA1 encryption, and the wireless is at "ath0".  Gnome's network-manager fails on encrypted wireless under Hardy, so that's out.  

I downloaded wicd.  It says it's using all the same settings that work under my non-GUI networking (wext for wpa, and so on), and it has the right wpa key.  But it will not connect.  

It looks like it may be trying to connect to "wifi0" instead of "ath0" (even though ath0 is the setting in the wicd-manager).  Oddly enough, the dmesg line about my Atheros chip says it's "wifi0"!  But everything that works connects to ath0!

What's going on?  Is there any way to get everything to understand that there's only one working wireless?  Or maybe this isn't why my wicd won't work?

:confused:

---

