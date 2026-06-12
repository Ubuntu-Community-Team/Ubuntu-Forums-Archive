---
title: "ndiswrapper in ubuntu server problem"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by brad8266 on 2008-08-18
Hi, I got ndiswrapper installed and the drivers running properly for my netgear wpn111 usb adapter and I can get it to successfully scan for signals and it finds all the networks around but I cant get it to connect to a network, plus the card seems like it shuts off every now and then as well. Im so close now. encryption WEP key was set also.

I know the card is Ok because I use it in the windows pc all the time.

---

### Post by brad8266 on 2008-08-18
bump... Anyone??

---

### Post by dmizer on 2008-08-18
Can you connect to networks without WEP?

---

### Post by brad8266 on 2008-08-18
> **dmizer said:**
> Can you connect to networks without WEP?

I will try that out in a while after I kill wep on the AP.

---

### Post by brad8266 on 2008-08-19
It works great unsecured I just found out. 

What is the proper command to set WEP??

---

### Post by dmizer on 2008-08-19
Take a look at this thread for more information: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

You'll probably get the best results by bypassing NetworkManager. Though the possibility exists that your driver simply can't support WEP.

---

### Post by brad8266 on 2008-08-20
It still wont connect with WEP, its weird because it does get an IP address from the router but wont go on the internet. Works fine unsecured though.

---

### Post by dmizer on 2008-08-20
If you get an IP with wep, can you ping google by ip or hostname?

Ping google by IP address:
```
ping 208.67.219.231
```

If you can ping google by IP address, then you may just have a DNS problem, and you can solve it by using OpenDNS servers: [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

