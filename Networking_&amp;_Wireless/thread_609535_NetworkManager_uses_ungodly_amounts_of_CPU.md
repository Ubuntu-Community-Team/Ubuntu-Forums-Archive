---
title: "NetworkManager uses ungodly amounts of CPU"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by Ademan on 2007-11-11
Well since installing Gutsy I've had quite a few problems, first off the network manager applet never seemed to detect my wired connection (eth0) yet it did in the liveCD, and things have been sloooowwwwww.  One day i popped into the system monitor and had a moment of epiphany, /usr/sbin/NetworkManager was eating up ungodly amounts of CPU at all times, i saw it go as high as 80% but it hovered around 30.  Well I googled a couple times and found nothing, and then today I tried googling again and lo and behold one of the first 5 results was this:  [http://ubuntuforums.org/showthread.php?t=535361](http://ubuntuforums.org/showthread.php?t=535361)  and it fixed my problem perfectly. Actually it fixed BOTH of my problems, it sees my eth0 (wired) and it no longer hogs my CPU.

 I suppose this isn't EXACTLY a call for help, but it is a support issue, and I was wondering how many people this affects, I didn't see any sort of entry on launchpad so i'll make one if necessary, but if anyone knows it's already there that'd be great to know.

cheers
-Dan

---

### Post by Anthony M on 2007-11-18
I having this same problem at times. Hopefully I can get it fixed.

---

