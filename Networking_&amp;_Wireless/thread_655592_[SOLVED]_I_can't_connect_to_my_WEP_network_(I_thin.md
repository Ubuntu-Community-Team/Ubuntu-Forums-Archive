---
title: "[SOLVED] I can't connect to my WEP network (I think this is keyring related)"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2008-01-01
I have a router that I've used with the same laptop and wireless adapter for over a year.  I've occasionally had to change the security type on the router from WEP to WPA and back again to accomidate for other hardware in the house.

For some reason, when I go to click on that network, the two circles with the spinning swirl thing only appears for a second, then reverts back to two computers and no connection.  It does not ask me to enter in a WEP key, or any key for that matter.

One thing I thought might be going on is Ubuntu see's the same SSID being used on the router, and assumes the security in use is WPA or something other than what it actually in use.  So I went into gnome-keyring-manager and removed all the keys...something I think I probably shoudl have not done.  Anyway, nothing has changed.  If I select other nearby networks that are secured, it asks for a password.  But that doesn't happen if I select my network.

Please help!

---

### Post by diablo75 on 2008-01-01
I got it fixed.

I went into ~/.gnome2/keyrings/ folder and renamed default.keyring to default.keyring.OLD.

:)

---

