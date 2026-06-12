---
title: "[SOLVED] lost wireless updating to 8.04 dlink dwl-g122"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by ncumming on 2008-05-10
For the past week or two i've been in upgrade hell trying to upgrade from 7.10 to 8.04.  I started trying through the upgrade manager, which failed half way through, then have gone through several rounds of booting to safe mode, using a live CD, upgrading via the alternate install CD, etc..., and finally have the desktop up and running.  I still don't think i'm 100% through the upgrade process, although when i try to upgrade off the CD it says i'm up to date.

the problem is that my usb wireless adapter isn't working anymore - its a D-Link DWL-G122.  I think part of the problem was that during a run of dpkg --configure -a it said there was an update recommended for my blacklist file - to remove the "blacklist rt2500usb" and replace it with something else.  I (probably studpidly) allowed the change and now my adapter doesn't work.  I tried blacklisting the driver again but with that line in the blacklist file ubuntu won't boot - it gets hung up on a regular boot "loading manual drivers," and booting to safe mode it gets hung up displaying the following:

usb 5-5: reset high speed usb device using eci-hcd and address 3

any ideas of how to get my adapter working again so i can keep working through this dist upgrade?  

what a pain!

---

