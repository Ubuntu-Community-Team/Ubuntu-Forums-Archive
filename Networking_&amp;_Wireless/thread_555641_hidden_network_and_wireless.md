---
title: "hidden network and wireless"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by yanouil on 2007-09-20
hello,

I have a big probleme with ubuntu and my wireless network with a WPA key.

When the network is not hidden, the network is OK. But when i Hide the network, ubuntu don't want to connect... :confused:


I have a double boot, and with windows XP in thi same computer all is OK. The driver of my wireless card is à IPW2200. My wireless network is an airport...


Does somebody have soe explanation about this bug???


PS : when i hide my network, me i can see it because I have activated my MAC adress.... Just, I see the network, but I cannot connect them, my WPA keys seem to be not reconized...

ps2 : sorry for my very bad english cause i am a little frenchy.... lol:lolflag:

THX

---

### Post by yanouil on 2007-09-21
nybody can help me???

 please....

---

### Post by alexjhart on 2007-10-11
I am having the same problem. Haven't found a solution yet.

---

### Post by Tundro Walker on 2008-01-17
I apologize for reviving an old thread, but I was having the same issue (IE: a WPA wifi connection works with an unhidden network, then won't work when the network is hidden.)

I did some googling, and found a [bug report in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214") that addresses this issue.  Looks like they're trying to down-stream the fix to Network Manager, so all distros using it will benefit, and it's slated to be fixed in Ubuntu by LTS version Hardy 8.04.  (I may be mis-reading the bug-report, though, so please correct me if I'm wrong here.)

---

