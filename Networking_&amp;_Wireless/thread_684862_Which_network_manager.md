---
title: "Which network manager?"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by meastaugh1 on 2008-02-01
I'm looking to deploy a batch of laptops (Asus eeepcs) with eeexubuntu. So far I've tried Network Manager and wicd, neither of which really do what I need. Are there any alternatives? These are my requirements:
The connect at startup success rate needs to be 95-100%, with auto-reconnect if connection is lost.
Supports WEP and WPA2.
Treats multiple APs on the same SSID as the same network.

The problems I've had with the managers I've tried so far is that manager prompts for keyring passwords at every connect. 

wicd is a vast improvement, but treats all APs with the same SSID as separate networks. This means entering encryption info for each AP (8-16) on each machine.

Any suggestions much appreciated.

---

### Post by jan quark on 2008-02-02
concerning the prompting manager

try this

[http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/](http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/)

---

