---
title: "AirLink101 AWLL3055 802.11G works on 7.14 liveCD!"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by wkulecz on 2007-07-29
AirLink101 Wireless 802.11G USB adapter AWLL3055 worked fine on Ubuntu 7.04 LiveCD boot up.  The salesman at Fry's said it was the same as the AWLL3025 except it had the +10dBi "patch antenna".   Good strong connection thru 4 walls about 30' away from access point.

Plugged it an after booting.  Had to disable the unconnected wired network and then configured the wireless eth1 using System->Administration->Network dialog.  Main quirk was it seemed my WEP pass phrase was too long.  Had to type it in as a hexadecimal string, then it worked after enabling DHCP

Hopefully the install will setup as easily.

--wally.

---

### Post by wkulecz on 2007-08-03
Follow up.  Installation went smoothly and the wireless 802.11G AWLL3055 has been problem free.

Only some usability issues in making the system fit for my very non-technical wife remain.

--wally.

---

### Post by icydragonclaw on 2008-01-25
Yo, I plugged it up and booted the Xubuntu 7.10 (64 bit) LiveCD and the little light did not come on.  So I unplugged it and plugged it back in, this got the light going.  I entered the appropriate information in Applications --> System --> Network, but I still did not have an ip address.  All I did to get it working was: sudo iwconfig eth1 essid NAME key KEY (where NAME and KEY correspond to the desired network) and then sudo dhclient eth1.

BAM, pulled an IP address and now I'm writing this :guitar:

P.s. I guess the adapter working in 7.10 would make sense as you got it working in 7.14, but I was having trouble with a netgear adapter and ndiswrapper so as this worked out of the box I felt I should mention that.

---

