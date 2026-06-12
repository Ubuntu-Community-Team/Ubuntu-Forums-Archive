---
title: "GNOME; Wifi keeps disconnecting almost immediately."
date: 2016-08-24
forum: Networking &amp; Wireless
---

### Post by mr.rotzak on 2016-08-24
Hello everybody, (I'm new in ubuntuforums, sorry for any mistakes)


I've installed Ubuntu Gnome, but keep running into difficulties concerning my Wi-Fi.
After I start up my laptop, the Wi-Fi is turned off. I can turn my Wi-Fi on by using 'Select Network' or 'Wi-Fi Settings', but every time the Wi-Fi is almost directly turned off (within one or three seconds). On one occasion I could briefly see my router, before the Wi-Fi was turned off once again. This suggests my wireless device can operate, but keeps being shut down.

**iwconfig **gives;

```
lo        no wireless extensions.

wlx0060b3373e89  IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
enp0s20   no wireless extensions.
```

I've tried;

sudo rfkill unblock all

at the same time I had Wi-Fi Settings turned on in the background. I could see that the switch for Wi-Fi turned on for a second, but turned off directly after.
I've searched the internet for a solution (for days now), but keep getting the same result.
Can anybody help?

Using a [LEFT]THOMSON TG123g 802.11g Wireless LAN USB Adapter gave the same results as my build in ZyDAS zd1211 wireless LAN Adapter.

[/LEFT]

---

