---
title: "Wireless and General Internet Problems"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by WolfCarinea on 2007-03-24
alright, 
I have a Compaq Presario R3000Z, with a Broadcom 4306 802.11b/g WLAN internal card, I've used Ndiswrapper to install both bcmwl5.inf and bcmwl5a.inf, Ndiswrapper says the device is present. IT STILL WON'T WORK!!! what the hell do i do?


Also, three days ago, my wired ethernet connection literally just stopped working, the Network Manager tries to use it to connect to the internet and gets nothing, it's set as a DCHI (or whatever that abrieviation is). I have been able to use it mulitple times, even switching back and forth between Windows and Linux, the connection still works just fine in Windows, just like the wireless.... it's acting the very same way, detected, activated, attempts to connect, and no results. ???? fix anyone?

ifconfig shows

eth0 Link encap:Ethernet HWaddr 00:0F:B0:6C:0F:88
UP BROADCAST MULTICAST MTU: 1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0b) TX bytes:0 (0.0b)
Interrupt:185 Base address:0x2000

lo Link encap:Local Loopback
inet addr: 127.0.01 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:255 errors:0 dropped:0 overruns:0 frame:0
TX packets:255 errors:0 dropped:0 overruns:0 frame:0
RX bytes:11272 (11.0KiB) TX bytes:11272 (11.0KiB)

---

### Post by Floppyjoe on 2007-03-24
For Network Manager to work properly you need to have all your network interfaces disabled in System/Administration/Networking.

Is there a button to press to activate your wireless card?
Did you blacklist the native driver for your wireless card?
```
sudo gedit /etc/modprobe.d/blacklist
```
add the line:
```
blacklist bcm43xx
```
then save and exit file.

---

