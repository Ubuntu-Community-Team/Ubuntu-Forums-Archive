---
title: "Is it possible to connect to 2 WiFi simultaneously?"
date: 2022-07-17
forum: Networking &amp; Wireless
---

### Post by erosman on 2022-07-17
I was wondering if it was possible to do so, to boost the speed. I have seen some articles about it but they were very old.
e.g. [How do I connect to multiple wifi networks?]("https://askubuntu.com/questions/488588/how-do-i-connect-to-multiple-wifi-networks")

---

### Post by #&amp;thj^% on 2022-07-17
If your card supports it, That link you posted is Ok to follow.

---

### Post by erosman on 2022-07-17
How do you check if the card supports it?

ThinkBook 15 G2 ITL

---

### Post by mIk3_08 on 2022-07-18
> **erosman said:**
> I was wondering if it was possible to do so, to boost the speed. I have seen some articles about it but they were very old.
e.g. [How do I connect to multiple wifi networks?]("https://askubuntu.com/questions/488588/how-do-i-connect-to-multiple-wifi-networks") Linksys WiFi speed booster works perfectly and it suits up your need. I'm not advertising Linksys it just that I have tried using it. And truly I observe that there is difference with the ordinary WiFi router compared to the WiFi speed booster. Regards and cheers.

---

### Post by erosman on 2022-07-19
Thank you mIk3_08 but the intension is to boost by combining 2 WiFi.



When I try

```
sudo iw dev wlan0 interface add wlan1 type station 
```

I get

```
command failed: No such device (-19)
```

---

