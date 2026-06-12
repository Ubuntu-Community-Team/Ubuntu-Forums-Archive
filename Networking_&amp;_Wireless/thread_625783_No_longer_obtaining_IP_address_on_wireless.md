---
title: "No longer obtaining IP address on wireless"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by Sawman on 2007-11-28
Hey folks, my wireless stopped retrieving IP addresses for some reason. It was working fine one day, then it stopped. I can still see the access points with WIFI radar or sys admin. but when I try to connect, it tries to get the IP but comes up with an error "Cannot get IP Address". Signal strength is good and no security key. Tried with several different routers.
Thanks in advance.

HP 5003cl
Ubuntu Studio 7.1
Broadcom 4318 with fwcutter

---

### Post by Sawman on 2007-12-01
Bump for help, please.

---

### Post by froy02 on 2007-12-01
type 'http://xxx.xxx.xxx.xxx" where xxx.xxx.xxx is your your router address which you can find in system>administration>network. It should be in the DNS tab and called dns server.

After you get in the router you can find all the computers hooked up to your router. I also suggest that you put a wep key because anybody can connect to your router when they are in range, VERY unsecured. They could put a wep key and you could not connect your wireless without it.  
To open open up the router the username is usually admin and the default password, you have to google it or check your manufacturer website.

---

### Post by tinycamp on 2007-12-01
are you using a wep key?

```
sudo iwconfig 
```

please, if youre going to post the output of the above, please **DELETE THE KEY FROM IT**, for your own safety

if so, then check its correct, cause it looks like that, also, please post the output of:

```
ifconfig
```

---

### Post by Sawman on 2007-12-01
No WEP key. No WPA key either.
It see's the router, but fails to obtain the IP address.

---

### Post by victorbrca on 2007-12-01
Have you tried to set up a static IP address no the PC to see if works?

vic.

---

### Post by Sawman on 2007-12-04
I have another post going because of permission problems with some files. As soon as I get this resolved, I will re-run fwcutter and see if reloading the drivers helps.
Thanks for the advice.

---

