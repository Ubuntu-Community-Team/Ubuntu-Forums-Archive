---
title: "Atheros Card detected but not working"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by abondi on 2006-09-21
Hello everybody.
I have an **atheros card** (Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)) installed in my computer, with ubuntu 6.06.

Kernel is 2.6.15-27-686, with **restricted-modules** installed.

Il I make *lsmod|grep ath* it display:
ath_pci                81852  0 
ath_rate_sample        17224  1 ath_pci
wlan                  146684  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148848  3 ath_pci,ath_rate_sample

instead doing *lspci|grep Ath* it comes out:
0000:03:0b.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

My network card **works in windows** but some time ago it stopped working with linux. I tried with every **combination of settings** for password, channel etc., so I'm asking if there's an **utility that logs** everything happens in the communication between network card and my router, so I can find where the problem is.

Thank you
Andrea Bondi

---

### Post by tturrisi on 2006-09-21
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

