---
title: "Wireless -Long delays"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by WolfJay_83 on 2007-10-21
I have Gutsy running with the "Restricted Modules" wireless driver ath_pci for the following wireless card:
00:08.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

I am using WEP 128bit encryption, and the D-link DI-624 router has all the "extra" features turned off - should be just plain wireless G.

The card connects quickly, ping times are fast (<10ms), and throughput is normal most of the time. However, the connection dies for several minutes at a time. The weird thing is that the pings still read as <10ms even when the ping has been sitting there stuck for over a minute.

How can the pings remain <10 ms even when I'm sitting there waiting over a minute for the ping to go through?

Anyone have this problem? I'm not even sure what the problem is, so it's hard to google.

---

### Post by Mundu on 2007-10-25
Same problem here. Same PCI card. Default auto configuration on fresh install.
Long delays. Slow performance even with signal strength reported as 40%.

---

### Post by Mundu on 2007-10-25
Editing the file /etc/rc.local as in the posting below seems to have fixed my problem:

[http://ubuntuforums.org/showthread.php?t=540101&highlight=ar5212]("http://ubuntuforums.org/showthread.php?t=540101&highlight=ar5212")

I  also switched to a static ip address (via manual wireless configuration). Click on the icon on the top right of desktop. That seems to 
have improved things drastically too.

---

