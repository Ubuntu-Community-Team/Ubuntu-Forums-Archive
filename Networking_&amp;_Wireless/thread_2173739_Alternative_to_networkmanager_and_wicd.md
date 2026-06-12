---
title: "Alternative to networkmanager and wicd?"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by zariskij on 2013-09-11
I've been using dell xps 13 ultrabook for almost a year. Wifi has always been a pain. It is extremely unstable and gets very slow after 10mins or so. I tried everything including 11n_disable, swcrpto, ipv6, etc...but nothing actually worked.

Now I found out that it is in fact a problem of network-manager. Today I manually connect wifi (iw and dhcpcd), and the wireless is super stable and fast. But since it is tedious (I work at several different places)to connect wireless manually, I removed networkmanager and installed wicd instead. However, although wifi under wicd is quite stable, it is weird that the speed is much lower. I tested the speed using speedtest.net at home, manual connection always got about 30Mbps-40Mbps while wicd connection never got 
above 10Mbps (I tested about 10 times).

So I am just wondering if there is any good alternative (gui preferred, but not necessary as long as it is convenient enough) to networkmanager and wicd? Thank you!

netctl seems to fit my need, but it doesn't look like it can be run on ubuntu? By the way, I am running 13.04.

---

### Post by TheFu on 2013-09-11
Write a script to swap config files and restart the different network daemons.
That's how we did it in the old days. [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

Speedtest is more about the WAN/Internet connection than wifi.
A few wifi troubleshooting tools exist.
* sudo wifi-radar
* sudo iwlist
* kismet
I find that using android tools to map out the wifi coverage is more convenient.  It is amazing what shifting 2 feet can do for coverage. Forget all the theories about wifi, If you really want to know where coverage is best, create a heat map for the possible locations you want to connect from.

---

