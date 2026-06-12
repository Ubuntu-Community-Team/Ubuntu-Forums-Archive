---
title: "Qualcomm QCA9377 wi-fi adapter suddenly not recognized anymore (Ubuntu 22.04)"
date: 2023-06-05
forum: Networking &amp; Wireless
---

### Post by sarmatia on 2023-06-05
Hello,  Ubuntu crashed to a slew of error messages in a TTY today (something to do with the hard disk, possibly -- can't remember the wording but "EXT4" came up a lot) and after rebooting, the wi-fi adapter (a Qualcomm Atheros QCA9377) is no longer "found" in Wi-Fi Settings. This problem has persisted as I upgraded Ubuntu to 22.04, tried installing the latest mainline kernel (6.3.6), tried installing new ath10k-firmware, and a few other things. Hope someone can help.    Here is the output of the wireless-info script: [ https://pastebin.com/AjfH4RZd]("https://pastebin.com/AjfH4RZd")    Kind regards!

---

### Post by jeremy31 on 2023-06-05
I would remove what was added to /etc/network/interfaces
Then in terminal ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo iwconfig wlp1s0 power off
sudo iwconfig wlp1s0 txpower 20
sudo iw reg set DE
```
Reboot

---

### Post by sarmatia on 2023-06-06
Worked perfectly, thanks! I noticed that Tw-Power seemed off (since it was set to INT_MIN or something) but wouldn't have thought of the rest.

---

