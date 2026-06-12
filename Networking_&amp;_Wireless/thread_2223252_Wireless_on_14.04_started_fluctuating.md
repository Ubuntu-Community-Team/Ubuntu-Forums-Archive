---
title: "Wireless on 14.04 started fluctuating"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by Teethdude on 2014-05-10
I noticed that my wireless randomly began to cut out. It claims to be connected, but I cannot visit any internet or network location. 
Here's my wireless card info:
```
mike@mike-Laptop:~$ sudo lshw -C network | grep driver       configuration: broadcast=yes driver=rtl8192ce driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.109 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
mike@mike-Laptop:~$ 
```

Every time it says "driver" it comes up in red. Not sure if that's an indicator of anything.

---

### Post by Teethdude on 2014-05-12
A nice person on Reddit gave me this: ```
[COLOR=#000000][FONT=verdana]echo iwconfig wlan0 power off | sudo tee /etc/pm/power.d/wireless
```
Not sure what it does, but it seemed to work.[/FONT][/COLOR]

---

