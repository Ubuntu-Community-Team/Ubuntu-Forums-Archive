---
title: "how to connect to internet in ubuntu 10.10"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by naved ..... on 2011-05-06
i have a wired internet connection , in win 7 i was using dial-up connection to connect to internet ..i have internal modem [no external modem ]
so how to connect to internet in ubuntu 10.10...? i tried but didnt succeded to do so !

so plz tell me that can i connect to internet or not ???
if yes than plz help

---

### Post by mr_luksom on 2011-05-07
Hi naved,

Internal laptop modems are generally 'softmodems' which rely heavily on propriety windows drivers to function. I personally tried to get one working with Mandriva in 2007 and failed miserably. If you are able to, an external modem/router is a better idea as they do not rely on propriety software, and will work correctly out of the box.

Having said that, if you would like to try to get your internal modem working the first step is to download and use the scanModem tool from linmodems.org. There is a lot of info at this site, and I suggest having a browse before starting (there are instructions on how to use the tool as well).

---

### Post by jtarin on 2011-05-07
[Another good source for Linux modem knowhow]("http://tldp.org/HOWTO/Modem-HOWTO-2.html").....if dial-up is your only option the investment in a good external modem will more than pay off.

---

### Post by ieee488 on 2011-05-07
> **naved ..... said:**
> i have a wired internet connection , in win 7 i was using dial-up connection to connect to internet ..i have internal modem [no external modem ]
so how to connect to internet in ubuntu 10.10...? i tried but didnt succeded to do so !

so plz tell me that can i connect to internet or not ???
if yes than plz help

Before I switched to DSL three years ago, I had AT&T dial-up, and I was able to get it working on Ubuntu 6.04.

The key is the modem. I was very lucky that my PCI modem was not a "Winmodem" and was detected in Linux, not just Ubuntu, but also OpenSUSE.
I can help you find an used PCI modem that works with Linux on eBay.

Anyway, **scanmodem** is must. [http://linmodems.technion.ac.il/first.html]("http://linmodems.technion.ac.il/first.html")

---

