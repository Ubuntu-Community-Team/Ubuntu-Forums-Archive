---
title: "Flaky WIFI with hidden ESSID"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by stefan) on 2005-10-24
After upgrading to Breezy my Thinkpad T42p's Atheros wifi became very flaky and is practically  not usable at my university. It works fine  with a norma and open AP but not with WEP and hidden ESSID.

Does the new driver have problems with hidden ESSIDs?
Does the new driver have problems with noisy environments?

I tried playing around with the rts and frags settings (via iwconfig) but without any reproducible results.

Anybody having similar problems or even a solution?

/stefan

---

### Post by stefan) on 2005-10-24
Another thing that might throw the new driver off is the fact that multiple APs are using the same ESSID. Anybody knows a bug with that?

I tried to force it to a specific AP by typing "iwconfig ath0 ap <MAC>" but again could not reproduce any improvement.

/stefan

---

