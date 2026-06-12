---
title: "Hardy + Wlan keeps dropping"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by wapsi on 2008-05-13
Hi.

I installed the newest version of Ubuntu (Hardy) and I've troubles with my wireless network connection:

Ubuntu (Dell C400 Laptop) connects to wireless network normally and ping is normal to Google or to my other lan-computers (latency etc...). The signal strength is excellent (80-98%) and transfer rate is 54m.

But I've a problem: after transferring some "bigger" files a few seconds the data stops moving ("bigger file =~ size over 2mb"). This thing appears with SMC-pcmcia (madwifi or ndiswrapper) and Alink-pcmcia (rt2x00/rt2500) too. I have tried change my wireless router (Dlink, SMC, Fonero) and wlan-router's configures (rate, B/G, open/wpa/wep, channel...) too but the result is always the same.

I also tried put ping to other terminal when I tranfer some files. The pinging stays normal although the transferring stops. It's very weird.

Today I compiled the newest versions of madwifi and rt2x00 but the problem still exists. I also removed 'network-manager' package too... No luck.

There is no problems with my WinXP computer's wlan and when my laptop is plugged to wired network everything works.

I'm old debian-user and there wasn't problem like this in Debian.

Thanks for help!

EDIT: I tried without ipv6-support/loading ipv6 on boot; The problem still exists.

---

### Post by maggiagg on 2009-01-27
Wonder if this is the same bug as [http://ubuntuforums.org/showthread.php?t=1030392](http://ubuntuforums.org/showthread.php?t=1030392) and actually several other reports.

---

