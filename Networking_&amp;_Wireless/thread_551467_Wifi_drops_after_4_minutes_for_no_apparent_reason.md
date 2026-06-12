---
title: "Wifi drops after 4 minutes for no apparent reason"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by benzs_s on 2007-09-15
Recently I moved house and the new router uses WPA rather than WEP encryption; I followed the tutorial for RT73 drivers and input the relevant WPA commands and everything was working fine... but after 4 or 5 minutes I won't be able to do anything internet-related ('sudo iwconfig' will come up with a blank essid after it drops, so ubuntu is aware of it) and will have to 'sudo ifconfig rausb0 down' then 'up' before inputting the WPA information yet again for it to work.

I'm writing this thread from a laptop using windows which has no such issues with dropping, so I'm fairly sure it's not the fault of the router or the internet, and it's certainly not a case of distance between the router and the PC with Ubuntu installed (the two are about 4 feet away!).

So yeah, I've no idea how to go about fixing this... the network is connected fine for a few minutes then will drop quite randomly and won't work again unless I restart the whole process. Any ideas?

---

### Post by stringkarma on 2007-09-24
I am having the same problem! It works fine about 10 mins then dies. I can fix it with down then up and it works fine another 10 mins. I suspect that some part of this is going into a powersave mode, but I am not sure.

---

### Post by DynamicMouse on 2008-06-07
I have the same problem here as well.  I am using a Zyxel G-260 with the NDisWrapper, a while ago I used the zd1211 (and zd1211rw) drivers and they didn't work.

I have attached a dmesg output, the connection was not working at 320.441225 and only started working again at 2230.170527.  The 'wlan0: link becomes ready' inbetween these times did not result in the connection becoming available and must have been the system lying to me :)

---

### Post by DynamicMouse on 2008-07-16
just in case this helps someone thought I'd post it.

I never got to the bottom of why my wifi connection simply dropped but did use a workaround that is quite simple.

As soon as I manage to get a successful connection to the router I start 2 pings going, one that repeatedly pings the router and another one that repeatedly pings [www.google.com](www.google.com).

So far this stops the connection from ever dropping, I left it connected for days and it didn't drop, I just wish I knew what caused it to drop in the first place.

---

