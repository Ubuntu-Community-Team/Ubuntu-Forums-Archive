---
title: "D-Link DWA-566 (Atheros AR9382) keeps disconnecting (Ubuntu 13.10)."
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by Lólindir on 2013-12-30
Hello!

I have a pc with a D-Link DWA-566 wireless network card in it. We have in our house an IEEE 802.11n network on a fixed channel (6) with WPA2-only protection enabled. Between the router and the pc is a repeater installed to improve the signal. The signal strength is most of the time between 40/70 and 48/70 (watch -n1 iwconfig).

When I keep the command above (watch -n1 iwconfig) running in a terminal window, than the network seems to disconnect and reconnect a lot. The network manger shows all the time a 'being connected' symbol, but when running the command above I can see it is actually disconnecting and reconnecting a lot (especially if the signal strength is getting lower). Downloads or streaming media are all the time interrupted.

The "invalid misc" variable is increasing rather rapidly as soon as I start downloading or watching e.g. something on youtube (from 0 to 150 in 1 or 2 minutes). Sometimes the variable "Tx excessive retries" is increasing as well (but only slowly and not so often). The lower the link quality, the higher the amount of "Tx excessive retries".

When starting-up windows 7 I don't have any network problems. Downloading or streaming media are working without any interruption.

I am using Ubuntu 13.10, but I have similar problems with Ubuntu 13.04.

Typical output of the command "watch -n1 iwconfig" is:
```
IEEE 802.11abgn  ESSID:"lolindir home network repeater"
Mode:Managed  Frequency:2.437 GHz  Access Point: 80:1F:02:C2:19:E0
Bit Rate=90 Mb/s   Tx-Power=20 dBm
Retry  long limit:7   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality=45/70  Signal level=-65 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:3  Invalid misc:179   Missed beacon:0
```


Anyone an idea what can be wrong and how to fix this?

Many thanks in advance!

---

### Post by praseodym on 2013-12-30
Try to deactivate the hardware encryption of the driver
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by Lólindir on 2014-01-21
Hi praseodym,

I've tried this now for a couple of weeks, but no significant improvement. I have the impression that, especially when there are other devices online (wireless), there are a lot of disconnects as described above, especially when the signal strength is below 40/70.

---

### Post by praseodym on 2014-01-21
Change the encryption mode in your router to pure WPA2-AES (CCMP) and a fixed channel

---

