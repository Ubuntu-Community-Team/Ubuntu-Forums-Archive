---
title: "network manager is ruining wireless connections"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by stanley drew on 2008-11-07
While cruising the forums to get my AR5007 card up and running (ath5k worked) I noticed that a lot of people have started to complain about slow and inconsistent connections. And in fact my connection has been awful since installing 8.10. I previously ran 8.04 with the madwifi ar5007 driver and used wicd to connect, but wicd isn't working for me in 8.10 so i'm stuck with network-manager just like everyone else.

Basically I think network-manager is the problem, because my roommate has a completely different hardware configuration on his laptop (he's 32-bit, i'm 64 and he has no atheros card), and he is running 8.04 but with the new network-manager and his connection sucks too. Does anyone agree with me and is there a way to revert to the old network-manager for now until they fix the new one?

As a separate issue, has anyone figured out how to make wicd work with my particular configuration (8.10, 64, ar5007)? Currently after installing it reads "Connected to  at -1%" but no wireless networks are shown. Wired connection works though.

---

### Post by stanley drew on 2008-11-20
So just to cap this off I did eventually get wicd to work in 64-bit intrepid. It turns out wicd wasn't detecting my wireless interface. After I added wlan0 as the wireless interface under preferences everything was fine. This solved the speed issue and the inconsistent connection problem as well.

---

### Post by harryfoster on 2008-11-20
Ok, well ive been searching the website for a while now and cant seem to find the proper driver downloads either. Hopefully ill be able to locate them otherwise i think i will have to purchase a new wireless card. Ive heard downloading something like windows sp3 can correct certain wireless connection problems. Is there any validity to that claim (im currently ruining sp2)?




_______________________________________________________

[Computer Support](http://www.nwcsupport.com/) |[ Network Management](http://www.nwcsupport.com/)

---

