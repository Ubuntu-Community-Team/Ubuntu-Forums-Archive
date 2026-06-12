---
title: "ZyXEL ZyAIR G-202  - any idea what chipset"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by dc2447 on 2007-01-25
Has anyone any idea what the [ZyXEL ZyAIR G-202](http://www.ebuyer.com/UK/product/122088) wireless usb dongle has for it's chipset and suggested driver?  Have searched in vain.

---

### Post by dc2447 on 2007-01-26
Well I am still trying to setup this usb wireless dongle

I have installed ndiswrapper and downloaded the windows drivers for my dongle

> ndiswrapper -l
Installed drivers:
wlanuzg         driver installed, hardware present


> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



> lsusb | grep Z
Bus 003 Device 007: ID 0586:3410 ZyXEL Communications Corp.

dmesg

> [17276404.176000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17276404.320000] usb 3-5: reset high speed USB device using ehci_hcd and address 7
[17276404.500000] ndiswrapper: driver wlanuzg (ZyXEL Communications Corp.,03/29/2006,6.6.0.0) loaded
[17276405.012000] wlan0: vendor: 'ZyXEL G-202 Wireless USB Adapter'
[17276405.012000] wlan0: ethernet device e0:fb:06:cc:e0:fb using NDIS driver wlanuzg, 0586:3410.F.conf
[17276405.012000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


I have tried disabled all encryption on my wireless network and getting wlan0 to dhcp but it never gets an address.

Any thoughts?

---

### Post by tturrisi on 2007-01-26
If you mean the ZyAir G220?
[http://zd1211.ath.cx/](http://zd1211.ath.cx/)

---

### Post by dc2447 on 2007-01-26
> **tturrisi said:**
> If you mean the ZyAir G220?
[http://zd1211.ath.cx/](http://zd1211.ath.cx/)


Nope G-202

[http://www.ebuyer.com/UK/product/122088](http://www.ebuyer.com/UK/product/122088)

---

