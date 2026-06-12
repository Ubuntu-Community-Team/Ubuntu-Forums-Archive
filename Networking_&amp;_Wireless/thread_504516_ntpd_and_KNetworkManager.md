---
title: "ntpd and KNetworkManager"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by exclipy on 2007-07-19
I want to sync my computer's time using ntpd.  However, ntpd requires an internet connection to be available and working when it starts up (ie. when the computer's booting).  Otherwise, it just sits there in the background doing nothing all day just because it couldn't find a server when it started.

KNetworkManager only initialises the network after KDE is up and running (I think the same applies for the Gnome equivalent).  This happens *after* ntpd starts, so my ntpd is always broken.

Is there a solution?  I want to continue using KNetworkManager.

---

