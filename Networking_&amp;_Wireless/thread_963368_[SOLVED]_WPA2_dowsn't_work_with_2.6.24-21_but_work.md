---
title: "[SOLVED] WPA2 dowsn't work with 2.6.24-21 but works with 2.6.24-20"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Rommidze on 2008-10-30
After upgrade to 2.6.24-21 NetworkManager fails to connect using WPA2. But it works if I boot using 2.6.24-20. Unprotected wireless works just fine under both kernel versions. My card is ipw2200.

**SOLVED:**
I have deinstalled linux-backports-modules-* packages and it works now. New backport package contained modules lbm_cw_ieee80211 and lbm_cw_ieee80211_crypt which were loaded automatically instead of proper ieee80211 and ieee80211_crypt.

---

