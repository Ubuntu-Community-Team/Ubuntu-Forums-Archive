---
title: "Wifi Dell 1450 Usb Adapter problem"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by marcel.patoulachi on 2005-11-08
hi,

i tried to install my Delll 1450 Usb Adapter without succes...could u please help me ?

here's what i did :

1. copy bcmwl5.sys and bcmwl5.inf to my desktop (founded on the net, got no windows partition)
2. ndiswrapper installation from source
3. ndiswrapper -i ~/Desktop/bcml5a.inf
4. sudo ndiswrapper -m
5. ndiswrapper -l 

> Installed ndis drivers:
bcmwl5          driver present

6. restart pc
7. modprobe ndiswrapper (seems ok, no errors messages)
8. dmesg

> ndiswrapper version 1.5 loaded (preempt=no,smp=no)

**9. iwconfig ... and here it doesn't give me the right result...my wlan0 isnt displayed !!!! shit !!! please help me !!!**

---

### Post by marcel.patoulachi on 2005-11-10
[fixed] yet my dell 1450 wifi adaptor is recognized...i use now the drivers from cd manufacturer and it seems ok.

althought i cant connect to my wifi ... i tried with dhcp and manual ip nothing change. i controlled my access point got the same channel (4) as my wifi adapter

into /etc/resolv.conf i got
nameserver 192.168.0.254

into /etc/network/interfaces i got
auto wlan0
iface wlan0 inet static
wireless-essid lalala
wireless-key **********
address 192.168.0.53
netmask 255.255.255.0
gateway 192.168.0.254

did i forget something ? the dns ? where ? who ?
please ... 

thanx

---

