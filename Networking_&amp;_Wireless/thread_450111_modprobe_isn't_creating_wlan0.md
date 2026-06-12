---
title: "modprobe isn't creating wlan0"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by Signal64 on 2007-05-21
I'm using 6.06.1 "Dapper Drake" and a Belkin USB F5D7050 Version 4 wifi adapter.

Version 4 uses the ZyDAS zd1211 chipset unlike Version 3 and earlier (which use Ralink Rt2x00).

When I boot, lsmod and dmesg doesn't show the zd1211 module.
modprobe -v zd1211 does load it and lsmode confirms it.

When I try ifconfig wlan0 up, there is no wlan0
ifconfig and iwconfig doesn't show any wireless adapters and there is no entry in /etc/network/interfaces

So the module isn't loading on boot.
When the module is loaded, it won't create a wireless device (wlan0).

I'm looking at trying to recompile the module but was hoping there is something else here that I maybe overlooking.

Any ideas?

---

### Post by Floppyjoe on 2007-05-21
Maybe try :
```
iwconfig wlan0 up
```

Just a guess.

---

### Post by Signal64 on 2007-05-21
Guess I wasn't clear enough in my topic or in this bit: > ifconfig and **iwconfig** doesn't show any wireless adapters and there is no entry in /etc/network/interfaces

There is no wlan0 to iwconfig with.

---

### Post by Signal64 on 2007-05-21
Update:  Adding wlan0 auto to /etc/network/interfaces still doesn't help.

ifconfig or iwconfig wlan0 up will claim there is no hardware present.

---

### Post by logos34 on 2007-05-22
> **Signal64 said:**
> I'm using 6.06.1 "Dapper Drake" and a Belkin USB F5D7050 Version 4 wifi adapter.

Version 4 uses the ZyDAS zd1211 chipset unlike Version 3 and earlier (which use Ralink Rt2x00).

When I boot, lsmod and dmesg doesn't show the zd1211 module.
modprobe -v zd1211 does load it and lsmode confirms it.

When I try ifconfig wlan0 up, there is no wlan0
ifconfig and iwconfig doesn't show any wireless adapters and there is no entry in /etc/network/interfaces

So the module isn't loading on boot.
When the module is loaded, it won't create a wireless device (wlan0).

I'm looking at trying to recompile the module but was hoping there is something else here that I maybe overlooking.

Any ideas?


You're probably going to have to use the vendor-based community driver to get it to work.  The zd1211rw driver that comes with pre-7.04 releases has problems.

You can dl the driver (rev. 85) **[here]("http://gentoo.osuosl.org/distfiles/?C=N;O=D")** among other places.  

**[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%287050%29%7C%28belkin%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%287050%29%7C%28belkin%29)**
**[https://help.ubuntu.com/community/WifiDocs/Device/Airlink101_AWLL3026?highlight=%28awll3026%29](https://help.ubuntu.com/community/WifiDocs/Device/Airlink101_AWLL3026?highlight=%28awll3026%29)**

---

