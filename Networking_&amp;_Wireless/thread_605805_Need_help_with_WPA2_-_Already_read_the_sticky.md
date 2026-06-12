---
title: "Need help with WPA2 - Already read the sticky"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by anonim on 2007-11-07
I'm using a clean installation of Gutsy Gibbon. I have an Atheros card which is using the ath_pci drivers. I can connect to my AP without security. However, I am unable to connect with WPA2 enabled.

I've read the sticky on wireless security and have edited my /etc/network/interfaces file:

> auto lo
iface lo inet loopback
auto ath0
iface ath0 inet dhcp
wpa-driver wext
wpa-ssid fiosap
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a

My AP is called fiosap. The SSID broadcast is set to off. I've copied the wpa-psk key above from the sticky because I'm at work now, but I did use the wpa_passphrase utility at home to generate the correct hex key based on my WPA2 key.

After editing the file, I restarted the machine. Unfortunately, I don't see a connection between the PC and the AP.

What are some troubleshooting steps I can follow?

---

