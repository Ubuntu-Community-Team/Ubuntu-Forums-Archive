---
title: "NetworkManager Applet 0.7.0 and WPA2"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by John.Gaythorpe on 2008-11-03
Okay so I upgraded Ubuntu and received NetworkManager Applet 0.7.0.

Great but now I cannot connect to my secure Wireless which is WPA2 Enterprise. 

Wireless works to unsecured networks, or WEP, but the applet "greys" out the "connect" after typing in all my information for WPA2 enterprise and NO MATTER what I put in there will not enable the "connect" button. 

What gives?

John.

---

### Post by John.Gaythorpe on 2008-11-07
Okay the village idiot is now usurped.

I found out the problem for me. I had to convert my certs and keys to PEM format using openssl.

Then I could get connected.

This was the major change between the NetworkManager applets, acceptance of certificate styles.

John.

---

