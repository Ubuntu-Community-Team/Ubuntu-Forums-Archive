---
title: "Netgear WG511T not working in Feisty"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by prensing on 2007-05-12
I have a Netgear WG511T PCCard (madwifi driver), but I just can't get it to work in Feisty. I am using WEP. 

When I first plug in the card, it scans for my home base station. It appears to find it. However, it can't manage to actually get an address on the network, presumably because it can't get WEP working. After a few seconds, it goes back to scanning, repeating the cycle "forever".

I did a lot of reading. I found lots of references to doing "iwpriv ath0 authmode 2". I have this set in a pre-up script and yes, it definitely changes the card's behaviour, but it does not solve the problem.

This card was working fine for me with Fedora 5. I then switched to Ubuntu 6.06 and saw this problem. At the time, I downloaded the last version of madwifi-old and installed it, and the card worked on the first try. 

Later I upgraded to Feisty and ran into the same problem. Unfortunately, installing madwifi-old did not work with Feisty, so now I am stuck.

I have even downloaded the latest SVN image from madwifi and compiled it, but no change. 

Please, having to compute while attached to Ethernet sucks. So any help would be appreciated. Would trying wpa_supplicant make a difference? If so, please point me to a HOWTO.

Thanks very much.

---

