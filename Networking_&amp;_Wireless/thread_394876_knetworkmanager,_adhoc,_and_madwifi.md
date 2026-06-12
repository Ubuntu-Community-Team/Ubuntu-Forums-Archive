---
title: "knetworkmanager, adhoc, and madwifi"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by goland55 on 2007-03-27
So I've got a laptop running feisty beta with the latest kernel and restricted modules (2.6.20.13) and I'm trying to use knetworkmanager to automatically switch to a totally open 802.11b adhoc network.  knetworkmanager lists the network essid in its menu but when selected, knetworkmanager will show progress up until 28% and then timeout.  If I check 'iwconfig ath0' at this time I can see the mode being changed between 802.11a, 802.11Ta, and 802.11g managed networks but never 802.11b or adhoc.

In contrast, I can issue iwconfig, wlanconfig, and iwpriv commands at the commandline and connect to the network without issue.  I want to be able to use some sort of easy-to-use gui to do this though as the rest of my family uses my laptop at times and I'd rather not have them issuing 'sudo' commands.

As of yet I've been unable to figure out if there is a limitation in madwifi, wpa_supplicant, or knetworkmanager.  I was hoping someone might have run into this problem and either knows the source of the issue or has resolved it.

Thanks.

---

### Post by spd106 on 2007-03-27
I'm not 100% on this, but I think the problem is that the madwifi driver isn't yet fully compatible with the wireless extensions tools. As the Network Manager team have stated that they don't intend to support anything else, that leaves us in the current state where we must use wlanconfig to switch to adhoc mode.

I have no idea when or indeed if madwifi will support switching mode through iwconfig any time soon.

I'm not a member of either of the dev teams, I am going by what I have used and read on the websites/mailing lists recently.

---

