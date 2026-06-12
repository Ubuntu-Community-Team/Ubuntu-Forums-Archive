---
title: "[SOLVED] Wireless connection does not auto-establish after boot"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by bmwman on 2008-05-31
After rebooting Ubuntu 8.04 the wireless connection previously established (WPA Personal) does not get established. I need to (a) change wireless WPA key to "blank", and then (b) back to the valid password, after which the wireless then connects and works fine.

I checked my network interface file and everything in there seems fine 
 /etc/network/interfaces

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-psk 9f11a4f2c689e94e0aaee2df003f46682bc6a9cf9bbacaaf058670d557d488de
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Trygg


Any ideas what's wrong?

Thanks

---

### Post by bmwman on 2008-05-31
Nobody??

---

### Post by bmwman on 2008-06-05
Maybe I need to rename the ath0 to wlan0 or wifi0?

No suggestions?

---

### Post by chili555 on 2008-06-05
This is a known fault or maybe bug in manually configured WPA. See post #2 here: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) 

I think the easier, workable solution is in post #1372 here: [http://ubuntuforums.org/showthread.php?p=4843394&highlight=rc.local#post4843394](http://ubuntuforums.org/showthread.php?p=4843394&highlight=rc.local#post4843394)

So, *sudo gedit /etc/rc.local* and add a new line above 'exit 0':```
/etc/init.d/networking restart
```Save and close gedit. Reboot. Did it start automagically?

---

### Post by bmwman on 2008-06-05
Thanks dude.Can't believe that's all it was. It's working now.

You're the man! :)

---

### Post by Wee Aldo on 2008-06-06
Seems to have worked here as well!

---

### Post by DeltaS on 2008-06-22
Another "thanks" to chili555 for the neat fix. Very frustrating to have a wireless system that works but won't start without jumping hoops.

---

