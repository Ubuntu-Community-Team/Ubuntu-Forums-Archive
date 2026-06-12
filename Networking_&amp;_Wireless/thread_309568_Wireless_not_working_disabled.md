---
title: "Wireless not working/ disabled"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by johnmxg12 on 2006-11-29
Hey guys i'm new to Ubuntu, but i went through the wireless trouble shooting guide and read several similar cases to mine but i havent found an answer to why my wireless card refuses to work in Ubuntu.  I believe the problem lies within enabling the device to turn on.  well here are some of the commands i've inputted into the terminal that'll help us solve my troubles. (sorry these are hand typed)

**iwconfig**

lo     no wireless extension

eth0   no wireless extension

eth1   IEEE 802.11 b/g ESSID:""Nickname "Broadcom 4318"
       mode: managed  Access Point: Invalid
       RTS thr: off  Fragment thr: off
       Link quality: 0  Signal level: 0 Noise level: 0
       Rx invalid nwid: 0 Rx Invalid crypt:0 Rx invalid'frag: 0 
       Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0

sit0   No wireless extensions

**cat /etc/network/interfaces**

auto lo
iface lo inet loopback

auth eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp 

auto wlan0
iface wlan0 inet dhcp

**iwlist scan**

lo     doesn't support scanning

eth0   doesn't support scanning

eth1   No scan results

sit0   doesn't support scanning

**ifconfig**

link recap: local loopback
inet addr: 127.0.0.1   mask: 255.0.0.0
inet lo addr: ::1/128  scope: host
up loopback running  mtu: 16436  metric:1
Rx packet: 18 errors: 0 dropped: 0 overruns: 0 frame: 0
Tx packet: 18 errors: 0 dropped: 0 overruns: 0 frame: 0
collisions:0 Tx quehelen:0
Rx bytes: 1284(1.2 KiB) Tx bytes:1284 (1.2 KiB

**sudo ifup eth1**
ifup: interface eth1 already configured

ok so i help this was informative about my wireless situation,  let me know if you need any other commands entered into my terminal,  thanks in advance to whoever's willing to help me. :)

---

### Post by trubblemaker on 2006-11-29
hey have the same card, can help you, no worries
pick an option from my signature and go for it,  you can use a native driver or a 'wrapped' windows driver.  ndiswrapper is faster,  native driver is slower but give you a more configuration options. If speed don't matter use the native. If you're a internet  eat and breath, use the ndiswrapper method.  If I could recommend the 'ndis from source' it's best for working for most people on the first try and it's about ten steps long.  For the native driver use the wiki howto
|
|
|
V

---

