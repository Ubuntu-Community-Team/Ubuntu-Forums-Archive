---
title: "Unable to use WPA with KNetworkManager (Dapper)"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by michaeljt on 2006-10-13
Hello,

I have so far been unable to connect to my WPA 1 encrypted wireless network using KNetworkManager.  I have a Netgear MA521 PC-Card adaptor with an rtl8180 chip.  The card is supported "out-of-the-box" by the Dapper kernel and wpa_supplicant (ipw driver), and I have been able to configure it so that I can connect using ```
ifup wlan0
```.

I have tried searching though the forums, but none of the advice on offer seemed to help.  I would be grateful for any suggestions!

Regards,

Michael

---

### Post by almax00 on 2006-10-13
launch knetworkmanager by kmenu -> internet -> knetworkmanager. after knetworkmanager launches you should see a new button in the bottom bar on the right by the clock. left click on the knetworkmanager button and a pane should open listing the available wireless networks you can connect to. click on your network and it should ask you for a WPA password. this is how i connect using knetworkmanager on dapper with a netgear 511t card.
good luck.

---

### Post by michaeljt on 2006-10-14
Thank you for the answer!  That is in fact what I did, but it prompts me for a WEP key, not a WPA key.  And even if I manually enter the network and encryption details, it fails to connect.  I know that the details are correct, since I have connected several other systems to this wireless LAN, and was able to connect my Kubuntu system without using NetworkManager.

I am interested though in trying to get it working the "official" way, and it might provide useful information for other people who try and are less happy with fiddling with the configuration files (if such people use Linux at all!)

---

