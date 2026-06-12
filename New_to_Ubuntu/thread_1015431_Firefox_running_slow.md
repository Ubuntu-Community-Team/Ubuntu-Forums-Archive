---
title: "Firefox running slow"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2008-12-18
Hey I was wondering if anyone could help me get firefox running faster again.  It's just been really lagging, and getting slower lately.  I know it's not my internet, cause I ran a speed test, and I'm getting what I'm supposed to be getting.  Does anyone know any tips that might help?

---

### Post by kansasnoob on 2008-12-18
> **Nazty_Nayt said:**
> Hey I was wondering if anyone could help me get firefox running faster again.  It's just been really lagging, and getting slower lately.  I know it's not my internet, cause I ran a speed test, and I'm getting what I'm supposed to be getting.  Does anyone know any tips that might help?

What version of Firefox? Click on Help > About and tell us!

---

### Post by Nazty_Nayt on 2008-12-18
It's 3.0

---

### Post by Mr Tim on 2008-12-18
What addons are you using? Is it possible that one of them is slowing down firefox? Try disabling them one by one (I know this can be a slow process). I had a terrible performance problem with the Fast Dial Extension.

---

### Post by mkvnmtr on 2008-12-18
There are acouple of options in preferences. Tell me if the site is a suspected forgery and tell me if it is an attack site. These can use a lot of time when their list get long. Adblocker can also get a very long list of sites to check. If you feel safe doing it try disabling them to se if you gain some speed.

---

### Post by Nazty_Nayt on 2008-12-18
Thanks guys, I figured out my problem.  Through a recent update my Moblock becomes active at start up.  Well once I turn it off, everything runs extremely faster.  Thanks for the help though guys.

---

### Post by jre on 2008-12-20
Indeed MoBlock blocks quite much traffic: That's its purpose, but it can be a pain, too.
In normal default installations outgoing traffic is REJECTED if it is blocked by Moblock. This makes sure that the sending application is notified immediately that its traffic was blocked (in contrast to DROPped packets, where no notification is sent). Verify via
```
sudo moblock-control show_config
```
if you have these settings:
```
REJECT="1"
REJECT_OUT="REJECT"
```

You also might reduce the number of used blocklists, and allow traffic to certain IPs or ports.


I just added this as a FAQ, see here:
[https://help.ubuntu.com/community/MoBlock#My%20internet%20is%20slow%20since%20I%20installed%20MoBlock](https://help.ubuntu.com/community/MoBlock#My%20internet%20is%20slow%20since%20I%20installed%20MoBlock)!

---

