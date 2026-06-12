---
title: "FYI: WlanAssistant bug and manual work around..."
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by elmerfud on 2007-11-01
WlanAssistant seems to have a bug whereby it loses the network from time to time.  While this is an issue, it isn't the real problem.  It seems to lose the ESSIDs too and will try to reconnect to the network using a non existant ESSID.  For me this non existant ESSID is that which was on another network, not the current network.

For example, this morning I was connected to the wireless router identified by "PeterAndJanette".  For some reason the connection was lost.  When I opened wlanassistant to reconnect, it scanned the network and found PeterAndJanette.  But when I tried to connect to "PeterAndJanette", it says "Connecting to linksys..."  The linksys router doesn't exist in this area.  Its from another area I connect to.  Thus the problem.

The way to manually connect using an ESSID is 

sudo iwconfig eth1 essid "PeterAndJanette" 
sudo ifup eth1

Manpages are your friend for more details.

I hope this helps someone.  I've asked the question how to manually boot a wireless network with a specific ESSID several times.  I found the answer today and I thought I would share it.

---

