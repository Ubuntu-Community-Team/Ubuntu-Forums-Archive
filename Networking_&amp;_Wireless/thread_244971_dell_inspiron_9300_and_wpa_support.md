---
title: "dell inspiron 9300 and wpa support"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by alterstill on 2006-08-27
Hi folks,

I am trying to setup my wireless network but again linux seems not to like me very much.
I have installed fresh copy of Dapper Drake, upgrade distro, than installed knetworkmanager. So far so good, I can connect to my network but unfortunatelly cannot ping my router.
One strange thing:
```
dmesg | grep ipw
```
shows:
```
[17179588.768000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179588.768000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179588.768000] **Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!**
[17179589.204000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179589.632000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)

```

Here is my iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"alternet"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:14:7C:AD:38:16
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-31 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:0   Missed beacon:0
```

Any suggestions?
Thanks in advance

alt

---

### Post by funchords on 2006-08-27
My install issues that warning, too, but I can connect.

Your wireless is looking good.  I think you are having a plain-ole networking problem.

What is the result of 'sudo ifconfig' and 'sudo netstat -r'?

---

