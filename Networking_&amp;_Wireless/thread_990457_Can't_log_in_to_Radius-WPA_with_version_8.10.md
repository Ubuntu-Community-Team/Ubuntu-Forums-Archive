---
title: "Can't log in to Radius-WPA with version 8.10"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by ArchWillie on 2008-11-22
I recently installed Ubuntu 8.10 on three laptops. Two of the four use different Wifi hardware (one uses ndiswrapper with an Linksys card and three are Dells with internal Broadcom hardware that usethe "wl" driver).

All of the laptops prevsiouy had Fedora F9 on them and all were able to connect to the Radius WPA connection in our office using network manager. None of them will conenct with Ubuntu 8.10.

Shown below is the entries from the /var/log/wpa_supplicant.log from the failed Ubuntu connection as well as the successful entries from Fedora installation.

**_Failed Connection_**

Trying to associate with 00:13:10:19:72:2b (SSID='Our Wifi' freq=2427 MHz)
Association request to the driver failed
Associated with 00:13:10:19:72:2b
CTRL-EVENT-EAP-STARTED EAP authentication started
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
EAP-MSCHAPV2: Authentication succeeded
EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
EAP-TLV: Earlier failure - force failed Phase 2
CTRL-EVENT-EAP-FAILURE EAP authentication failed
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys


**_Good connection_**

Trying to associate with 00:13:10:19:72:2b (SSID='Our Wifi' freq=2427 MHz)
Associated with 00:13:10:19:72:2b
CTRL-EVENT-EAP-STARTED EAP authentication started
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
EAP-MSCHAPV2: Authentication succeeded
EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
WPA: Key negotiation completed with 00:13:10:19:72:2b [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:13:10:19:72:2b completed (auth) [id=0 id_str=]

Both are trying to connect via Network Manager and both have that same login screen pop up.

Any ideas?

Thanks!

Arch

---

