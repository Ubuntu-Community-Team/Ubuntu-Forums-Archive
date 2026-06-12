---
title: "Wireless only sometimes connects"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by card_ace on 2011-08-18
Alright so I have a Dell inspiron laptop dual booting windows 7 and 11.04, both 64 bit. Windows has no problems getting online our secured network. But for some reason my ubuntu only sometimes picks up wireless networks. I'm in a dorm and can pick up a dozen wireless networks on windows but ubuntu doesn't see any of them. Wireless is turned on and just says disconnected. Also, both here and in other places some times I turn it on the wireless works perfectly. Other times it doesn't work at all. Any suggestions will be great!

---

### Post by jfed on 2011-08-18
Normally I would say you didn't install the correct wireless card drivers...but that fact that it does work, but only sometimes is confusing to me. Here, do this for me me quick. Go to System>Administration and look for "Additional Drivers"

If thats there, good. Click on it, and after it 'searches for available drivers' and see if it lists anything with the word "wireless" in it.

If it does, you probably have to install that driver. If it has multiple, (or none at all) feel free to report back here.

---

### Post by card_ace on 2011-08-19
Yeah it doesn't make sense to me. When I check the additional drivers page there's only one "broadcom STA wireless driver" and I've already installed that. 9 out of 10 times it doesn't work, but once in a while it does.

---

### Post by card_ace on 2011-08-20
alright this is very interesting now.  if i'm in windows and shut it down and restart into ubuntu the wireless doesn't pick up any networks.  But, if I just put windows on "hibernate" then go into ubuntu then it connects right away and I can pick up the other networks around my dorm.  So i guess problem solved, but now i'm just curious about why its happening

---

### Post by akoskm on 2011-08-20
> **card_ace said:**
> alright this is very interesting now.  if i'm in windows and shut it down and restart into ubuntu the wireless doesn't pick up any networks.  But, if I just put windows on "hibernate" then go into ubuntu then it connects right away and I can pick up the other networks around my dorm.  So i guess problem solved, but now i'm just curious about why its happening

Not sure why is this happening to your but I have similar experiences with my gf's laptop which is also in dual booting mode. There by default setting windows switches the wireless/bluetooth card off on shut down, but in such way that I even can't start it again from Ubuntu. :D However, changing wireless/bluetooth settings in windows solved the problem.
Maybe you should take a look at your wireless setting in Windows too.

---

