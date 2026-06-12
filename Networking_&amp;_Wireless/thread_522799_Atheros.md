---
title: "Atheros"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by MagicCow on 2007-08-11
I am completely new, have no background knowledge, so I will need everything spelled out. That being said, I am trying to get my wireless card working. It's a dlink dwa-542. Uses the Atheros chipset. I have ndiswrapper, when trying to install in GUI, it freezes. When trying to install via terminal, everything seems to go fine, says drivers are installed, and device is found. However when i type iwconfig wlan0, I get "wlan0: no such device." 

zach@ubuntu:~$ ndiswrapper -l
net5416 : driver installed
        device (168C:0023) present
zach@ubuntu:~$ iwconfig wlan0
wlan0     No such device


Any ideas?

---

### Post by marsmissionaries on 2007-08-11
NDISWRAPPER WILL NOT WORK. it WILL freeze everyt ime.


You need to install the latest version of madwifi here: [http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2650-20070811.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2650-20070811.tar.gz)

It will need to be compiled from source.

The version of the atheros chipset you have it not supported under feisty by ndiswrapper so yo will need to use the latest madwifi snapshots.

I have this exact same card in my desktop pc.

---

### Post by MagicCow on 2007-08-11
Ah! Thank you, this will hopefully relieve much frustration.

---

