---
title: "Wireless up and running, but cant connect to wpa"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by brujoand on 2006-08-21
hey i have a broadcom bcm4306 chipset. At first I couldnt get the wireless card running, this fixed that [http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm4306)

But, now i cant connect to my wpa encrypted network.

iwconfig gives:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"bridgefield"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```
and iwlist eth1 scann gives:
```

eth1      Scan completed :
          Cell 01 - Address: 00:11:50:39:40:E7
                    ESSID:"bridgefield"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-155 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 52ms ago

```

Im running a fresh install of dapper, on a dell inspirin 5150. 
Any clues on what to do? I cant find a post that helps.
Thanx

---

### Post by crxyem on 2006-08-21
did you install wpa_supplicant ??

---

### Post by brujoand on 2006-08-21
yeah, Im trying to use wpasupplicant, but I cant really figure out how use it.. 
i tried

```
wpa_supplicant -Dndiswrapper -ieth1
```
but nothing happens..
Then i tried 
```
wpa_supplicant -Dndiswrapper -ieth1 -c/etc/wpa_supplicant.conf
```
but theres no config file there.. Yeah, i cant really understand this thing..

---

