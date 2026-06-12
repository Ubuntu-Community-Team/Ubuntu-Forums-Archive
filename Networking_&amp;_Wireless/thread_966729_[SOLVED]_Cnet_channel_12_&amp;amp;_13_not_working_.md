---
title: "[SOLVED] Cnet channel 12 &amp;amp; 13 not working in Intrepid"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by leifjonny on 2008-11-01
My cnet wireless card only scans channel 1-11.
With Hardy this could be fixed by adding the line:

options mac80211 ieee80211_regdom=64

to

/etc/modprobe.d/options

If i do this in Intrepid wlan0 interface disappear.

---

### Post by leifjonny on 2008-11-02
Fixed it.
Apparently the line for the 2.6.27 kernel is:

options cfg80211 ieee80211_regdom=EU

---

