---
title: "Controling a dialup connection"
date: 2004-11-19
forum: Networking &amp; Wireless
---

### Post by pref-at-laval on 2004-11-19
I failed to get my linmodem to work so I purchased an external USR 56K Spedster. I connected it in and used the network GUI to set up my ISP account. It all worked perfectly the first time.

I have a limited amount of hours I can connect to my ISP every month so I would like to connect only when I need to get my mail or do some surfing. Unfortunately, it seems that Ubuntu as set up by default tries to keep connected all the time. As soon as I de-activate the modem (in the network GUI) it hangs up but re-dials immediately after. Turning off the modem (hardware with the switch) works but when I turn it back on later, it does'nt re-dial.

Is there an easy way to connect and disconnect whenever I want to?

---

### Post by zenwhen on 2004-11-19
Install "gnome-ppp" and give it a shot.

---

### Post by mr_ed on 2004-11-23
Or use pppconfig and pon/poff (via the GNOME Modem Lights applet)

---

