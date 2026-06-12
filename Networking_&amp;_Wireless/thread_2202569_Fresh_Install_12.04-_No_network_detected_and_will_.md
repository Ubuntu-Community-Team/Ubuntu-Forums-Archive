---
title: "Fresh Install 12.04- No network detected and will not detect wired connection"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by chris154 on 2014-01-29
Hi.

This is my first time trying Ubuntu and I am hitting some problems.  I cannot connect to the internet.  When I click the wifi icon, it says no network devices available, and it wont find any wireless networks.  I tried a wired connection, and it still will not connect to the internet.  In system settings>network, It says "Wired- Cable unplugged".  Any ideas?

This is a Late 2012 Apple Macbook Pro (Retina)

If you need any terminal checks, which do you need?

---

### Post by Iowan on 2014-01-29
Post results of:
```
ifconfig -a
sudo lshw -C network
```

---

