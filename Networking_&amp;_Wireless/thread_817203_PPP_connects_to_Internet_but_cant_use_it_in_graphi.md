---
title: "PPP connects to Internet but cant use it in graphical apps"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by marcog123 on 2008-06-03
Hello,

Im running Kubuntu 8.04. Im using a 3G USB modem and i can connect to the Internet usign KPPP. In the console (with kconsole) i can easily resolve names and ping addresses. 

I have normal route and ifconfig output shows ppp0 normally with ip address. When i try to use firefox, konqeror, kmail, etc... they dont work.

Strangely enough, if i put firefox in OFFline mode it works, also in KnetworkManager -> Options -> Show Connection Information it reports "No active device"....

---

### Post by comandrei on 2008-06-03
Try configuring you connection with 
```

sudo pppoeconf

```
in Konsole.

---

### Post by marcog123 on 2008-06-04
Hi,

if i run sudo pppoeconf it only shows up eth0 and wifi0 as active devices, it does a unsuccefull scan on each, and it closes.

Maybe, i'm doing something wrong....but else...if i use kppp, and i get connected to the Internet, why isnt it detected by the apps running on the desktop only on console. Weird!

---

