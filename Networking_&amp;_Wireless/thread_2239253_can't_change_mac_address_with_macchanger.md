---
title: "can't change mac address with macchanger"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by beelzebufo on 2014-08-12
I can't seem to change my mac address with macchanger anymore, I used to do it all the time, but that was on a different machine, here is what I do:

```
wreckingball@wreckingball-PC:~$ sudo ifconfig wlan0 downwreckingball@wreckingball-PC:~$ sudo service network-manager stop
network-manager stop/waiting
wreckingball@wreckingball-PC:~$ sudo macchanger -r wlan0
Current MAC:   64:5a:04:56:90:5d (Chicony Electronics Co., Ltd.)
Permanent MAC: 64:5a:04:56:90:5d (Chicony Electronics Co., Ltd.)
New MAC:       64:5a:04:56:90:5d (Chicony Electronics Co., Ltd.)
It's the same MAC!!
wreckingball@wreckingball-PC:~$ sudo macchanger -m 11:33:55:44:22:66 wlan0
Current MAC:   64:5a:04:56:90:5d (Chicony Electronics Co., Ltd.)
Permanent MAC: 64:5a:04:56:90:5d (Chicony Electronics Co., Ltd.)
[ERROR] Could not change MAC: interface up or insufficient permissions: Cannot assign requested address



```

It looks like I have some permissions problems, but I am running as root, so, I shouldn't have any permissions issues unless ubuntu has started userproofing their OS and I don't think they would do that, could it be locked by the manufacturer?  I am running on a dell inspiron 15r-5537 laptop.  Thanks in advance

Beelzebufo

---

