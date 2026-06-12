---
title: "broadcom, gutsy upgrade, and suspend oddities"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by ayu on 2007-12-30
Hi, I just made the upgrade to Gutsy on my Dell Vostro, (was using ndiswrapper in Feisty, installed via a script posted on these forums), and was stuck a while on the restricted drivers firmware.  I went ahead and downloaded [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) from [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) as the firmware to use.  
When I first boot up my computer, it will take around 10 minutes of connecting/disconnecting before it is successful.  Resuming from suspend, the connection is always re-established within half a minute.  After a while, I realized network manager says it using the bcm43xx driver upon a clean boot, but ndiswrapper upon resume from suspend.  Other people on these forums also note that the restricted drivers firmware is not as good picking up signals as ndiswrapper, and seeing how I already have ndiswrapper working, I went ahead and disabled the restricted driver.  However, now when I boot up my computer it doesn't see the wireless until i do a suspend and resume! Any ideas on what to do? 
Thanks

---

### Post by ayu on 2008-01-02
bump :)

---

### Post by ayu on 2008-01-15
I am now using another wireless router, but for some reason, the essid shows up as "". It sometimes works after resuming from suspend, and manually "Connect to other wireless network", and entering the essid and key several times.  Giving up on this daily 15 minute ritual just to connect, I am currently using a external wireless card, but would really like to use my laptop wireless if at possible.  Please help!  Thank you

---

### Post by ayu on 2008-02-02
Could somebody please help me!  I don't want to keep using an external wireless card!  Any ideas why my home router essid shows up as "" with my internal wireless? And yes, my internal wireless does function properly at other locations.

---

### Post by ayu on 2008-02-11
b-b-b-bump! :)

---

