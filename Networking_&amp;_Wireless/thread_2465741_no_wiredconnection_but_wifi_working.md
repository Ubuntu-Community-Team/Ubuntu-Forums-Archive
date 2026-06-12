---
title: "no wiredconnection but wifi working"
date: 2021-08-10
forum: Networking &amp; Wireless
---

### Post by planchiste on 2021-08-10
Hello, 
I am currently a quite old Asus computer (but working fine with a SSD) with ubuntu 20.04 and windows 10 on a dual boot. I have internet with both wifi and wired connection on windows but only wifi on ubuntu. In the settings &#8594; Network, there is only "Cable unpluged" (while of course it is still pluged in).
Can you help me ?

---

### Post by TheFu on 2021-08-12
What is the card chip used? Are the correct drivers loaded?  Does it work if you soft reboot?  Does it work only after a hard reboot?  When testing the wired connect, be certain to disable the wifi.

This command will tell us which chip and driver are being used:
```
inxi -Nnxz
```
If there isn't any driver found, it it a bigger issue.

---

