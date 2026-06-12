---
title: "error on airodump"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by markomk on 2008-11-30
ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig eth2 up; iwconfig eth2 mode Monitor channel <#>'

how can i fix this?

---

