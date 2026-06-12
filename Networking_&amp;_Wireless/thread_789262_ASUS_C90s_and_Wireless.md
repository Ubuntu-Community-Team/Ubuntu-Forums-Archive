---
title: "ASUS C90s and Wireless"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by ace141 on 2008-05-10
first of all, sorry for my bad English.

I have installed the windows driver of c90s with ndiswrapper, but the wireless card doesn't work. the LED is always turned off.

the chipset is atheros ar5008

output of the wireless card:

```
filippo@filippo-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:off/any
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated

Bit Rate:54 Mb/s
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

filippo@filippo-laptop:~$ ndiswrapper -l
netathw : driver installed
device (168C:0024) present
filippo@filippo-laptop:~$ sudo ifconfig wlan0 up
[sudo] password for filippo:
filippo@filippo-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:off/any
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated

Bit Rate:54 Mb/s
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

filippo@filippo-laptop:~$ iwlist wlan0 scan
wlan0 No scan results //but windows find  connection
 
```

thank you

---

### Post by ace141 on 2008-05-10
nobody?

---

