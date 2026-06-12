---
title: "How do I remove madwifi modules"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by okos on 2008-05-11
I need to upgrade and patch the madwifi driver for my pcmcia wireless card.
However, before I do that I need to remove the old madwifi modules.
How do I do that without messing up my system?
I don't think that I can just delete them.
I also do not see it listed on the synaptic package manager.
On the other hand, I can see that the card does show up in lspci and knetwork manager.
I cannot find the package source on my system.


> 
$locate madifi
/lib/modules/2.6.24-16-generic/madwifi
/lib/modules/2.6.24-16-generic/madwifi/ath_pci.ko
/lib/modules/2.6.24-16-generic/madwifi/ath_rate_amrr.ko
/lib/modules/2.6.24-16-generic/madwifi/ath_rate_minstrel.ko
/lib/modules/2.6.24-16-generic/madwifi/ath_rate_onoe.ko
/lib/modules/2.6.24-16-generic/madwifi/ath_rate_sample.ko
/lib/modules/2.6.24-16-generic/madwifi/wlan.ko
/lib/modules/2.6.24-16-generic/madwifi/wlan_acl.ko
/lib/modules/2.6.24-16-generic/madwifi/wlan_ccmp.ko
/lib/modules/2.6.24-16-generic/madwifi/wlan_scan_ap.ko
/lib/modules/2.6.24-16-generic/madwifi/wlan_scan_sta.ko
/lib/modules/2.6.24-16-generic/madwifi/wlan_tkip.ko
/lib/modules/2.6.24-16-generic/madwifi/wlan_wep.ko
/lib/modules/2.6.24-16-generic/madwifi/wlan_xauth.ko


Any help would be much appreciated.

---

### Post by chili555 on 2008-05-11
Can you simply remove *linux-restricted-modules*?

---

### Post by okos on 2008-05-11
> **chili555 said:**
> Can you simply remove *linux-restricted-modules*?

I removed the comments updated apt-get and madwifi isnt in the synaptic manager.

---

### Post by chili555 on 2008-05-11
> I need to upgrade and patch the madwifi driver for my pcmcia wireless card.I guess I thought you had an updated package in mind. Your question was how to remove madwifi and I think removing *linux-restricted-modules* does it. Did you try? Did it remove madwifi?

---

