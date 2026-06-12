---
title: "Please help me with my WMP54G v4.1/RT61"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by KARaidl on 2008-02-01
I've read over countless guides, and I'm all out of ideas. A few weeks ago I was happily surfing and downloading at blazing speeds using the RT61 driver for my Linksys WMP54G v4.1 wireless card, rather than the RT61pci driver included in Gutsy. But then I did a clean install and now I can't seem to repeat that former success.

The RT61pci works well... when it works. It won't automatically connect and the connection will sporadically drop out, so I wanted to switch again back to RT61. I followed this guide - [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo) - although I skipped the step about the minor modification using Gusty as I figured it would be unnecessary seeing as the RT61 driver on the Ralinktech website has since been updated, and sure enough, the module compiled just fine.

Anyway, I did everything the guide told me to and now "iwlist ra0 scan" turns up several different access points including the one I want to join. I've set up my interfaces file to use DHCP, but so far, I can't get an internet connection anymore.

Keep in mind that I'm writing this on Windows as it's my only way on the internet, so downloading WICD, Wifi Radar, or Ndiswrapper, is all out of the question, but didn't even work the last time. (Trust me, I've followed a LOT of guides.)

I'd just like a decent suggestion on what to configure and how to properly do it. But please keep your instructions in noob-friendly speak. (I'm fine with using the command line and I'd think that would be easiest.)

---

