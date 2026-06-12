---
title: "Dell Precision 5520 (XPS 15 equiv) wifi power"
date: 2018-04-13
forum: Networking &amp; Wireless
---

### Post by ghetto2ivy on 2018-04-13
My Wifi card is using way too much power. 

Wifi disabled powertop reports 4.5W total system draw at basically idle.
Wifi enabled powertop reports ~32W system draw at basically idle.

lsmod reports these drivers: 
iwlwifi               249856  1 iwlmvm
cfg80211              614400  3 iwlmvm,iwlwifi,mac80211

any idea how to get my Wifi draw down?

---

