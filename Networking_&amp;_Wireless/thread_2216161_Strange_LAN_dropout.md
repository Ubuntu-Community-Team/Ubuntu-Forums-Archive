---
title: "Strange LAN dropout"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2014-04-10
Three times in the past two days, I've experienced a strange loss of connectivity on my little LAN, which at present has only two live stations (but a number of VMs on each, all operating in bridged mode). In all three cases, I have been viewing, using VBox's vrdp capability and rdesktop, larger-than-usual E-mail messages that are stored in a VM on one station, but being viewed on the other's host system, and have been scrolling the screen when suddenly the E-mail program freezes and connectivity between the stations is completely gone. Attempts to ping one from the other, in both directions, fail with "network is unreachable." Using ifdown and ifup has no effect, and neither does restarting both machines.

When I move to the machine that has the mail VM running, that VM appears to be totally frozen -- but I am able to force it to be saved, and later restore it with no visible damage.

And powering down the original viewing station, letting it cool down for 10 minutes or more, then bringing it back up, has restored flawless operation in all three cases. Normally, both machines run 24/7, and neither has indicated any signs of overheating previously; both report constant temperatures, using Thunar's sensor plugin and hdtemp, in the area of 40 degrees C.

My initial diagnosis is that the network adapter that serves the LAN connection in the "viewing" station is getting itself into an "impossible" state for some reason, but I've not found any information in my logs to support this idea, and "the usual suspects" for diagnostic tools aren't showing me anything unusual.

My question, at this point, is precisely **which** logs, configuration files, and/or diagnostic tools will be most likely to help me determine what is happening? Both machines run Xubuntu 12.04.4, fully updated. Both received the *openssl* update immediately prior to these symptoms appearing, which seems a bit suspicious, but I've not seen any reports of problems with it. All suggestions will be welcome!

---

### Post by JKyleOKC on 2014-04-12
bump

---

### Post by JKyleOKC on 2014-04-20
bump -- please see also [http://ubuntuforums.org/showthread.php?t=2218091](http://ubuntuforums.org/showthread.php?t=2218091) which is the latest status of the problem...

---

