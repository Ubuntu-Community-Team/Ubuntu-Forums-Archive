---
title: "Wireless Signal Issues"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by Tikiman on 2007-12-18
Right, so I checked a few other threads but didn't find anything conclusive, so I figured I'd post here.

I'm a brand new user to Ubuntu, using a dual-boot on my laptop before I take the plunge to go all the way. Things have been a little rocky, but I'm finally ready to try using Ubuntu all the time. Here's the problem... usually I'm at my campus where there's a strong, fast network set up. However, at times I'll go to my parents' house where the network is weak in many parts.

Bottom line, in Windows Vista my laptop can pick up the signal with 1 or 2 bars... but in Gutsy I can't connect at all... sometimes it shows no network, sometimes it shows the network but just loops trying to connect. I can connect when there's a stronger signal... but this is an issue.

I'm using an HP dv6258se with a Broadcom wireless card... installed using the tutorial and that program thinger (bwcutter maybe?)

Any help would be appreciated!

---

### Post by spd106 on 2007-12-20
Unfortunately there isn't much that can be done to help at the moment.

There has been a lot of progress on the bcm43xx driver and the Linux wireless system in general over the last few months, but these changes will not hit Ubuntu until the next release.

One alternative is to use ndiswrapper with the Windows driver. Many people have reported better speed and range using ndiswrapper. The installation isn't too hard, but there are a few tricky bits to watch out for. For example you'll have to disable the bcm43xx driver before you load ndiswrapper.

See the help wiki for more [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by GSF1200S on 2007-12-20
> **spd106 said:**
> Unfortunately there isn't much that can be done to help at the moment.

There has been a lot of progress on the bcm43xx driver and the Linux wireless system in general over the last few months, but these changes will not hit Ubuntu until the next release.

One alternative is to use ndiswrapper with the Windows driver. Many people have reported better speed and range using ndiswrapper. The installation isn't too hard, but there are a few tricky bits to watch out for. For example you'll have to disable the bcm43xx driver before you load ndiswrapper.

See the help wiki for more [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I have a broadcom card on my second lappie, and it picked up signals far better with ndiswrapper than the bcm43xx driver- if you need the range, definitely go for ndiswrapper..

---

