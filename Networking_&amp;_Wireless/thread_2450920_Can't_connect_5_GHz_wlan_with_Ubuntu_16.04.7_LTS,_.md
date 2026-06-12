---
title: "Can't connect 5 GHz wlan with Ubuntu 16.04.7 LTS, Windows&amp;Android works"
date: 2020-09-23
forum: Networking &amp; Wireless
---

### Post by larik2 on 2020-09-23
Hello

When trying to connect on my Fujitsu Lifebook S761 with Ubuntu 16.04.7 LTS to wlan on 5 GHz channel (office_wlan 5 GHz) the system asks for wifi password. There is no password and my Android phone and a Windows laptop connect without it. I've tried with the password that is used in the Office_wlan without success. Does this have anything to do with Ubuntu wlan?


In the wireless-info I noticed following. Does this have to do with the problem?
```
[14217.644012] wlan0: authenticate with <MAC 'Office_wlan 5GHz' [AC7]>
[14217.646723] wlan0: send auth to <MAC 'Office_wlan 5GHz' [AC7]> (try 1/3)
[14217.753030] wlan0: send auth to <MAC 'Office_wlan 5GHz' [AC7]> (try 2/3)
[14217.753499] wlan0: authenticated
[14217.757044] wlan0: associate with <MAC 'Office_wlan 5GHz' [AC7]> (try 1/3)
[14217.758219] wlan0: RX AssocResp from <MAC 'Office_wlan 5GHz' [AC7]> (capab=0x411 status=0 aid=4)
[14217.760472] wlan0: associated
[14217.808720] wlan0: Limiting TX power to 23 (23 - 0) dBm as advertised by <MAC 'Office_wlan 5GHz' [AC7]>
[14220.765652] wlan0: deauthenticated from <MAC 'Office_wlan 5GHz' [AC7]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
```

Thanks for the help.

---

### Post by praseodym on 2020-09-23
Please run the wireless script from the sticky thread and show the outputs

---

