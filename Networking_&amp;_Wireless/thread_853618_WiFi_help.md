---
title: "WiFi help"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by axxjaj on 2008-07-08
Hi I'm a newbie and cannot connect to my Orange Livebox WiFi. I can use the wired connection however. I have upgraded to 8.04, and can post below the iwconfig result. The connection manager shows all the wifi networks in range 9including my Livebox) but after entering the WPA key the swirly thing swirls but never connects, I would really welcome some easy to follow guidance - many thanks !

[LIST]
[/LIST]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:A4:71:BC:08   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2008-07-09
I was reading this: [http://www.thekirschners.com/articles/orange-livebox-review.html](http://www.thekirschners.com/articles/orange-livebox-review.html) and was especially interested in this:> To connect a device to the wireless network for the first time you have to press a little button on the back of the LiveBox. This is a good thing as is provides a decent protection level against WiFi pirating. When a red light starts to blink I initiated the connection and it worked. This procedure only has to be performed the first time you connect a device. The LiveBox remembers the MAC address of the connected device which afterwards will be able to connect without restrictions.Did you try this?

---

