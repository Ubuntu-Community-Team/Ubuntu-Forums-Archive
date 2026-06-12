---
title: "Realtek rtl8188ee Wifi Card"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by awhb87 on 2014-02-04
How's it going everybody? I running Ubuntu 13.8.0-35 on an HP Envy 15 with a RealTek 8188EE WiFi card. I got my WiFi card working at home with backports-3.12-1. Now I'm back at college and I can't seem to maintain a stable WiFi connection with the campus wireless. Fantastic right? I'm trying to connect to a WPA2 with PEAP. I can connect to the access point no problem, but the internet phases in and out, with a lot more out than in. This problem persists as well with the campus' PSK WiFi option. 

Your assistance would be greatly appreciated.

---

### Post by varunendra on 2014-02-06
It may be an old bug in Network Manager where it keeps hopping over different access-points when there are too many available with same SSID. We may try a workaround which is crude but at least it may confirm if the problem is indeed that bug or something else.

Check available access-points with "**sudo iwlist scan**" command. Then try saving the MAC ID of the access-point with strongest signal into the "BSSID" field of Network Manager settings for the connection. Save and close the settings and see if it makes the connection (with that particular access-point) stable.

If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by awhb87 on 2014-02-07
FYI, I'm out of the town where the error is occurring, I should be able try the fix, or if need be, provide the information requested on Sunday.

---

