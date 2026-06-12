---
title: "mac80211 and ieee 802.11 puzzle with rtl8187L"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Buster95 on 2008-08-14
From my searches on this site (and other reading), I understood that release 8.04 contained a native rtl8187 driver that uses the mac80211 stack, where on earlier releases, they were configured for ieee 802.11.

I also understood that if both mac80211 and ieee 802.11 drivers were loaded, a conflict could arise, causing the wireless to misbehave.

Well, my wireless misbehaves appallingly, so while hopefully clutching at this straw.......

"lshw -C network" shows ieee 802.11 under wireless while "lsmod" records the rtl8187 module, both separately and in association with mac80211.

How can I tell whether my wireless system is using the mac80211 associated rtl8187L driver and not an ieee 802.11 associated rtl8187 driver from a previous release?

---

