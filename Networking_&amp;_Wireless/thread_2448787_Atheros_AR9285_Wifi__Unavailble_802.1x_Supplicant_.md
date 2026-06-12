---
title: "Atheros AR9285 Wifi : Unavailble 802.1x Supplicant failed"
date: 2020-08-13
forum: Networking &amp; Wireless
---

### Post by josephtj on 2020-08-13
Wifi drop issue used to occur in 20 mins interval earlier. Now wifi drops in less than 10 mins

I have attached file with iwconfig output when connection was live and disconnected.
Somone please help me.


Regards
Joseph
[COLOR=#000000]


[/COLOR]

[COLOR=#000000]
[/COLOR]

---

### Post by CelticWarrior on 2020-08-13
Thank you for the attachment. However the script in this section sticky is more useful to troubleshoot this sort of issues: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by josephtj on 2020-08-13
i have attached wireless info to the thread.

---

### Post by CelticWarrior on 2020-08-13
You need to change the router's settings like... NOW!

Only use WPA2-AES, not any WPA/WPA2 mixed mode and certainly not TKIP (roughly quoting chili555 from memory), deprecated a long time ago, insecure and horrible with some chipsets in Linux.

Also, why did you installed WICD?

Lastly, you may benefit from setting your own country instead of the 00 (Global).

---

### Post by josephtj on 2020-08-14
Hi
I have made the changes as suggested by except the country country code.. i could not find it where to change. Wifi disconnection happens inless than 5 mins. WICD was installed as suggested one of the forum. have removed it completely using sudo dpkg --purge wicd wicd-gtk

---

### Post by josephtj on 2020-08-14
issue has worsened from morning. wifi i regularly use is not detected now when i tried to connect to net. dependant on ethernet cable or usb tethering from mobile now.

---

### Post by josephtj on 2020-08-14
iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

---

### Post by CelticWarrior on 2020-08-14
What else have you done?

Other then simply not using WICD, an piece of old software crap (whoever suggested that should be arrested LOL), all the other changes suggested were at the router/AP and all suggestions are the currently accepted "best practices". WPA2 only and encryption type AES (some other names are the same, the main point is to NEVER EVER use TKIP) can only make everything better, i.e., this machine and all the other clients in that network regardless of hardware an OS.

---

### Post by josephtj on 2020-08-14
No other chnanges done. Wifi has returned on starting after a nap of 3 hours.

iwconfigeth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11  ESSID:"JKLLeena"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: B8:19:04:D3:74:39   
          Bit Rate=81 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0

---

### Post by CelticWarrior on 2020-08-14
Please run the script again to see what other things it might be complaining of.

---

### Post by josephtj on 2020-08-14
Wifi dropped in about 10 mins. Using mobile usb tethering.

iwconfigeth0      no wireless extensions.


lo        no wireless extensions.


usb0      no wireless extensions.


wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by josephtj on 2020-08-14
Wifi lost in about 10 mins. Using mobile usb tethering.

iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


usb0      no wireless extensions.


wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by josephtj on 2020-08-16
Hi
I misread your response hence the delay. Attaching script result run now.

---

### Post by josephtj on 2020-08-19
Used a spare wirless adapter and wifi working like a breee. Thanks to all who supported & guided.

---

