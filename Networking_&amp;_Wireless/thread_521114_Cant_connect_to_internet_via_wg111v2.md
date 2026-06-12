---
title: "Cant connect to internet via wg111v2"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by PoisoN2003 on 2007-08-09
Hey when ever i try to connect to my network i get this

    SET failed on device wlan0 ; Operation not permitted.

---

### Post by prof_booty on 2007-08-20
I am encountering a similar error with my wg111v2, can you reproduce it? Have you figured out a solution?

I followed the directions at [http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html](http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html)

The exact error I get is 

prof@paradox$ sudo iwconfig wlan0 essid ssid channel 11g key [deleted]

Error for wireless request "Set Frequency" (8B04)
SET failed on device wlan0; operation not supported

I'm going to try a few things when I get home tonight, but perhaps we can compare notes.

---

### Post by prof_booty on 2007-08-21
I managed to get this to work:

1. enable ssid broadcast on router

2. disable wep/wpa on router

3. change to mixed mode (b/g)

4. sudo iwconfig wlan0 essid xxxxx

5. reverse steps 1 & 2

5. sudo iwconfig wlan0 essid xxxx key xxxxx

I didn't have to pass the channel arg to iwconfig to connect.

---

