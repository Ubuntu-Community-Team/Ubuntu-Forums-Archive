---
title: "pon - setting idle disconnect time"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by jodef on 2005-08-07
I have an external serial modem which ubuntu seems to have some problems properly detecting. Only pon / poff seem to work correctly. That is ok I guess my only concern i since it runs in a terminal and I am on dial up easy to forget it is running in background wasting valuable internet time.

I need to set a idle time disconnect ie if my internet connection is idle for 5 minutes to auto disconnect.

Can this be done?

---

### Post by jasmuz on 2005-08-07
Yes, trough "pppconfig". To do so just type sudo pppconfig at the terminal or console, and edit your current connection.

---

