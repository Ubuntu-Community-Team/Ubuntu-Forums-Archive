---
title: "Transfer Settings from KNetworkManager to wpa_supplicant"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by Reverend_Morgan on 2007-09-17
I am currently using NetworkManager to connect to my university wireless network. My problem that is that the connection keeps getting dropped and I have to manually reconnect every few minutes. The NetworkManager daemon frequently dies and I have to restart that, too.

I would like to use wpa_supplicant to manage the connection, and have spent hours tinkering with the protocols and encryption, but no joy.

Anyone know how to find out what settings NetworkManager is using so that I can configure wpa_supplicant properly?

I'm using a WG311EEv3 network card with ndiswrapper and the XP drivers. KNetworkManager is configured like this:

Encryption: WPA Enterprise
EAP Method: PEAP
Phase 2: NONE
WPA Version: WPA1

---

