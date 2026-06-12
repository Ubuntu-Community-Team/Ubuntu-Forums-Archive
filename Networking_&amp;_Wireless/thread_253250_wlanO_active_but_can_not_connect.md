---
title: "wlanO active but can not connect"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by muggins on 2006-09-08
After many days trying to get my wireless usb adapter recognized I finally succeeded.Hurray. Now I can't connect to server even though wlan0 is active.I also have windows xp on same machine and have no problems connecting with it. Is there something I may still need to configure?

---

### Post by amo-ej1 on 2006-09-08
So the device show up, does it get an ip address ? are you wireless parameters configured (essid, wep key, ....) ? can you ping the wireless router ?

---

### Post by muggins on 2006-09-08
Yes I do have an ip address and parameters are configured but cannot ping the wireless router.

---

### Post by amo-ej1 on 2006-09-08
you have them configured in a static way or using dhcp ? 

another nice application for wireless devices is 'wavemon'  (sudo apt-get install wavemon and after that execute (wavemon wlan0). It show signal quality, signal to noise ratio and such to troubleshoot level 2 issues 

(at least if wavemon isn't broken, as it is on my laptop :'( )

---

