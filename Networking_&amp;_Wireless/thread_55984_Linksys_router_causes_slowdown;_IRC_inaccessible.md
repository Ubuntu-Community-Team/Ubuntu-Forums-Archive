---
title: "Linksys router causes slowdown; IRC inaccessible"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by WAM on 2005-08-10
I got a Linksys WRTP54G wireless+ethernet router and installed it. Now, websites load slowly, I can't use IRC, etc. but a [speed test](http://www.speakeasy.net/speedtest/)  still shows my bandwidth as normal. I've tried a couple things.

1) QoS - HTTP & 113 as high-priority
2) Port forwarding
3) Port triggering
4) DMZ

None of them work. At all. Then again, I'm not sure I did them right.

However, and here's what's really pissing me off, everything works fine on my laptop set up with wireless on WinXP. 15m away pages load blazingly fast and mIRC works just fine.

---

### Post by adwait on 2005-08-11
Hmm.......Try turning off ipv6 in /etc/modprobe.d/aliases. Also, check the /etc/resolv.conf. It should have your DNS servers listed and not your router IP address.

---

### Post by WAM on 2005-08-12
Hm. I haven't tried disabling IPv6 yet (do I just comment out the line about IPv6?) but my resolv.conf is like... blank. This is all it says. 
```

search (network name)
nameserver (router IP address)

```
IRC works now by the way... it just started working... magically,

Commenting out the line about IPv6 didn't do anything.

More info on symptoms: it will take a long time to load a page (google) the first time, but then it will go at a normal speed for every new search term. Odd.

---

### Post by adwait on 2005-08-12
No you don't just comment the line. You replace the word ipv6 with off. ie:
alias net-pf-10 ipv6 becomes
alias net-pf-10 off

---

### Post by WAM on 2005-08-15
Turning off IPv6 doesn't do anything.

---

