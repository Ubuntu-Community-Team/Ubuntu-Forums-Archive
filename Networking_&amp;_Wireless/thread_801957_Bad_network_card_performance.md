---
title: "Bad network card performance"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by thedarkleaf on 2008-05-21
I'm using a Belkin 802.11g Wireless card, and the connection keeps dropping in and out, seemingly as if the signal is poor.

However, I have a dual boot machine, and annoyingly there seems to be no problem whatsoever getting a signal in windows XP. 

How is that even possible? I thought if it were a driver issue then it would not work all the time, not only some times. Can the driver affect the performance?

I have recently upgraded to ubuntu 8, but i started having this problem a few weeks before the upgrade. I tend to use Windows now whenever I need to get online (like now).

Any suggestions?

Thanks.

---

### Post by bluefrog on 2008-05-21
if you are using a restricted driver from ubuntu, try using windows driver (with ndiswrapper) or vice-versa.

---

### Post by prshah on 2008-05-21
> **thedarkleaf said:**
> I'm using a Belkin 802.11g Wireless card, and the connection keeps dropping in and out, seemingly as if the signal is poor.


Try turning off power saving on the wireless device:```
sudo iwconfig wlan0 power off txpower fixed
```

Replace wlan0 with your actual wireless interface.

---

### Post by thedarkleaf on 2008-05-21
Thanks, I changed to using the windows driver with ndiswrapper, and since rebooting haven't been disconnected at all. If it starts to happen I'll post again, but if not we can assume all went well! Thanks!

ps: i tried switching the power saving off as well, but my device apparenlty doesn't support that feature. Thanks for the idea though.

Cheers!

---

