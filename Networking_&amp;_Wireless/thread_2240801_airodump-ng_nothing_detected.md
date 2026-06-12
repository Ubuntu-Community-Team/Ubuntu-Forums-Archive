---
title: "airodump-ng nothing detected"
date: 2014-08-22
forum: Networking &amp; Wireless
---

### Post by bouha on 2014-08-22
Hi i installed my Netgear A6100 wifi usb mini adapter yesterday with help from this forum: [http://ubuntuforums.org/showthread.php?t=2240631](http://ubuntuforums.org/showthread.php?t=2240631)

My problem is when i use airodump-ng i detect nothing.

with ```
airmon-ng
``` i got this: 

```

Interface    Chipset        Driver

wlan1        Unknown     rtl8812au - [phy1]
wlan0        Intel 5100    iwlwifi - [phy0]

```

i want to use the wlan1

with ```
airmon-ng start wlan1 
``` i got:
```
Found 6 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
770    avahi-daemon
774    avahi-daemon
977    NetworkManager
1064    wpa_supplicant
2362    dhclient
2481    dhclient
Process with PID 2362 (dhclient) is running on interface wlan1
Process with PID 2481 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan1        Unknown     rtl8812au - [phy1]
                (monitor mode enabled on mon0)
wlan0        Intel 5100    iwlwifi - [phy0]


```

killed all the processes that would cause problem with

```
airmon-ng check kill
```

and when i use ```
airodump-ng mon0
```

i got: ```
CH  0 ][ Elapsed: 0 s ][ 2014-08-22 14:05                                     
                                                                               
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                               
                                                                               
 BSSID              STATION            PWR   Rate    Lost    Frames  Probe 

```

after few secs it becomes ```
 CH -1 ][ Elapsed: 36 s ][ 2014-08-22 14:06                                    
                                                                               
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                               
                                                                               
 BSSID              STATION            PWR   Rate    Lost    Frames  Probe 
```

with nothing detected at the end, in addition i can't turn it into managed mode with ```
iwconfig wlan1 mode managed
``` or with ```
ifconfig wlan1 down
iwconfig wlan1 mode managed
ifconfig wlan1 up
```

i must inplug then plug it manualy to make it mode managed

---

### Post by overdrank on 2014-08-22
Hi and welcome. If you were to do a quick search of the forums you would see [_this_]("http://ubuntuforums.org/showthread.php?t=2228994&p=13046605#post13046605") .
Thread closed

---

