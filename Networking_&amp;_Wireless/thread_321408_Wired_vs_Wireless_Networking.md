---
title: "Wired vs Wireless Networking"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by The Minder on 2006-12-18
Newbie here.

Have a Tyan box running Ubuntu Edgy with Firestarter and Webmin and providing file sharing via Samba and IP addressing via DHCP.   The server has two network cards, one to the internet via DSL and the other to a managed 24 port switch.   Also connected to the switch are 7 Win XP boxes plus a Smartbridges Wireless Access point.   I have 6 wireless clients access the system through the Access point.

The wired boxes connection to group and private directories on the Ubuntu box can best be descrbed as 'flacky' and drop off at fairly short intervals (anywhere from 1 to 30 minutes) but there's no problem with their connection to the internet.

The wireless clients on the other hand have flakey internet connections.   They can't see the group/public holders on the server because they don't have linux/samba credentials.

In Webmin, looking at DHCP connections, none of the wireless IPs are listed, just the wired boxes... methinks that is strange.

I don't know where to start.   I thought that as the wireless clients were coming in through the switch to the DHCP server (and getting a legitimate IP address) they would be visible in Webmin... but not so.

Two questions (and the obligatory plea for help).   First, should not the wireless clients IP show up in Webmin.   Second, is there a chance Firestarter is screwing things up.   Firestarter installed like a breeze and I've never received any error messages from it.

Advice/comments/answers would really be appreciated.

---

### Post by scrooge_74 on 2006-12-18
A note on Firestarter there is a good howto on how to correct some problems with SAMBA due to the firewall

[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

On the other question, I don't have an answer for you, I don't use webmin that much so I cant help there.  just an idea, from your box can you get into the Access point and see the wireless clients? So you can rule that out?

---

### Post by The Minder on 2006-12-18
Thank you scrooge.

From my main Win XP box I can access the smartbridges and see the mac addresses of my wireless clients.   Using other windows based software I can also see the IP addresses these clients are being given by the Ubuntu DCHP, so I know (as best I can) that that side of the house is ok.   I have no idea how to access the smartbridges from within Ubuntu Edgy.

I'll check out the link you provided... thank you.

---

