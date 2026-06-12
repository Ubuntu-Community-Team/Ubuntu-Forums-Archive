---
title: "Wireless (WPA) on compaq nc8000"
date: 2005-06-25
forum: Networking &amp; Wireless
---

### Post by independence on 2005-06-25
I'm having some problems getting my WPA encrypted networking to work on my laptop. I have a Compaq nc8000 laptop with a Atheros wireless card.
Ubuntu found the interface ath0 and I could use it with no encryption. But when I installed wpa_supplicant it told me that the driver couldn't enable WPA. I searched google a bit and found out that I needed a newer driver. So I followed this guide: [http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972) to get the latest driver.
Everything went smoothly and I didn't have any problems, but when I restarted. The computer couldn't find the interface ath0 anymore. I looked in dmesg and saw that I had the new driver (0.9.14.9), but there was a lot of error messages after that. The messages look like:
ath_pci: disagrees about version of symbol ath_*
ath_pci: Unknown symbol ath_*
ath_* is ath_rate_tx_complete, _ath_hal_attach, etc
Please help me! :)

---

### Post by independence on 2005-06-26
I managed to get it to work now :)
I recompiled wpa_supplicant with the new madwifi driver.
I wrote a little howto in case I hade to do it again some time, maybe someone else will find it useful. You can find it here: [http://marcusson.no-ip.com:8080/wpa_madwifi_howto.xhtml](http://marcusson.no-ip.com:8080/wpa_madwifi_howto.xhtml)

---

