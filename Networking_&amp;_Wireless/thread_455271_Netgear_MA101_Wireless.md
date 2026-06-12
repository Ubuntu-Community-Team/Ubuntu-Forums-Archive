---
title: "Netgear MA101 Wireless"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by jaggexy on 2007-05-26
Am new to Linux, Can't get connection to network using above usb adapter in Feisty Fawn. Lsusb recognises adapter and iwconfig shows
```
wlan0     IEEE 802.11b  ESSID:"mynetwork"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Assumed this is a driver issue ? This adapter uses Atmel chipset(Rev B for AT76C503A), I downloaded a driver file called atmelwlandriver-3410tar, but have not clear what to do next if that is indeed the issue. Can you help ?

Under lshw :
```
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:09:5b:31:b2:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.2-84 wireless=IEEE 802.11b
blackbox@blackbox-desktop:~$ 

```

And under dmesg:
```

ubuntu/wireless/at76/at76c503.c: 2522: assertion dev->istate == INIT failed

```

---

### Post by jaggexy on 2007-06-12
In the end I bought a US Robotics usb adapter for twenty euro, plugged it in and everything works fine now:D

---

