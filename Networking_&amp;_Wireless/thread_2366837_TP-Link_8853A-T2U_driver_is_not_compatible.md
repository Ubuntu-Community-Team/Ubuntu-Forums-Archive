---
title: "TP-Link 8853A-T2U driver is not compatible"
date: 2017-07-22
forum: Networking &amp; Wireless
---

### Post by time_racer on 2017-07-22
Hey,

I got this USB-wireless adaptor from TP-Link and am trying to use it on ubuntu 17.04 but when i downloaded the original driver from TP-Link from its side it is meant to support only upto kernel 3.16 the details of the adaptor and OS is as following:
> 
[I]uname -r
4.10.0-28-generic
[/I]
> 
[I]lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 148f:761a Ralink Technology, Corp. 
Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/I]

> 
[I]dmesg
[ 5383.980030] usb 1-6.1: new high-speed USB device number 9 using ehci-pci
[ 5384.103514] usb 1-6.1: New USB device found, idVendor=148f, idProduct=761a
[ 5384.103517] usb 1-6.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 5384.103519] usb 1-6.1: Product: WiFi
[ 5384.103520] usb 1-6.1: Manufacturer: MediaTek
[ 5384.103522] usb 1-6.1: SerialNumber: 1.0[/I]


> 
[I]
iwconfig
lo        no wireless extensions.

enp4s0    no wireless extensions[/I]


[http://paste.ubuntu.com/25145918/](http://paste.ubuntu.com/25145918/)


I would appreciate your assistance in this case

---

### Post by chili555 on 2017-07-22
Here is some guy that thinks it just might work. Try it and let us hear back: [https://askubuntu.com/questions/865102/tp-link-t2u-ac600-usb-wlan-adapter-driver-on-ubuntu-16-10](https://askubuntu.com/questions/865102/tp-link-t2u-ac600-usb-wlan-adapter-driver-on-ubuntu-16-10)

I just tried to compile it on my 17.04 system and it 'makes' with a few warnings but no errors.

You will need a temporary internet connection and also:```
sudo apt-get update
sudo apt-get install git
```

---

### Post by time_racer on 2017-07-23
hi, i tried this before, with no luck. I did it again also, same issue

---

### Post by chili555 on 2017-07-23
> **time_racer said:**
> hi, i tried this before, with no luck. I did it again also, same issueMeaning what? It doesn't compile? It compiles but doesn't create a wireless interface? It created a wireless interface but won't connect? Sparks? Smoke? Locusts??

---

### Post by praseodym on 2017-07-23
[http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218](http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218)

This one compiled up to kernel 4.4. Higher kernel versions not tested here...

---

### Post by time_racer on 2017-07-24
> **chili555 said:**
> Meaning what? It doesn't compile? It compiles but doesn't create a wireless interface? It created a wireless interface but won't connect? Sparks? Smoke? Locusts??

it was successfully compiled but the interface is not being recognized 

iwconfig
enp4s0    no wireless extensions.

lo        no wireless extensions.

iwlist scan
enp4s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

---

### Post by time_racer on 2017-07-24
> **praseodym said:**
> [http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218](http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218)

This one compiled up to kernel 4.4. Higher kernel versions not tested here...


it is the same it is supporting only upto kernel 3.16  as stated in the link [http://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver](http://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver)

---

### Post by praseodym on 2017-07-24
I was able to compile it with 4.4, however, due to the lack of suitable hardware it is untested ;)

---

### Post by chili555 on 2017-07-24
> **time_racer said:**
> it was successfully compiled but the interface is not being recognized 

iwconfig
enp4s0    no wireless extensions.

lo        no wireless extensions.

iwlist scan
enp4s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.Are there any interesting messages?```
cd mt7610u
sudo insmod mt7610u.ko
dmesg | grep -e rt2 -e mt76
```

---

### Post by time_racer on 2017-07-26
I got the following outputs:

> sudo insmod mt7610u.ko 
insmod: ERROR: could not insert module mt7610u.ko: Unknown symbol in module


> dmesg | grep -e rt2 -e mt76
[88224.998391] mt7610u: loading out-of-tree module taints kernel.
[88224.998798] mt7610u: module verification failed: signature and/or required key missing - tainting kernel
[88224.998833] mt7610u: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[88224.998857] mt7610u: Unknown symbol cfg80211_scan_done (err 0)
[88224.998879] mt7610u: Unknown symbol regulatory_hint (err 0)
[88224.998901] mt7610u: Unknown symbol wiphy_new_nm (err 0)
[88224.998909] mt7610u: Unknown symbol cfg80211_connect_bss (err 0)
[88224.998922] mt7610u: Unknown symbol wiphy_register (err 0)
[88224.998947] mt7610u: Unknown symbol wiphy_unregister (err 0)
[88224.998975] mt7610u: Unknown symbol ieee80211_channel_to_frequency (err 0)
[88224.998991] mt7610u: Unknown symbol ieee80211_frequency_to_channel (err 0)
[88224.999003] mt7610u: Unknown symbol wiphy_free (err 0)
[88228.694493] mt7610u: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[88228.694522] mt7610u: Unknown symbol cfg80211_scan_done (err 0)
[88228.694549] mt7610u: Unknown symbol regulatory_hint (err 0)
[88228.694574] mt7610u: Unknown symbol wiphy_new_nm (err 0)
[88228.694585] mt7610u: Unknown symbol cfg80211_connect_bss (err 0)
[88228.694601] mt7610u: Unknown symbol wiphy_register (err 0)
[88228.694632] mt7610u: Unknown symbol wiphy_unregister (err 0)
[88228.694665] mt7610u: Unknown symbol ieee80211_channel_to_frequency (err 0)
[88228.694685] mt7610u: Unknown symbol ieee80211_frequency_to_channel (err 0)
[88228.694700] mt7610u: Unknown symbol wiphy_free (err 0)


---

### Post by chili555 on 2017-07-26
> insmod: ERROR: could not insert module mt7610u.ko: Unknown symbol in modulePlease see the end of another long mt7610u thread here at post #49. [https://ubuntuforums.org/showthread.php?t=2366669&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2366669&highlight=mt7610u)> In fact, having tried many different versions of mt7610u from github and other sources, I am unaware of any driver that compiles successfully and then works; that is, connects and pulls web pages, emails, etc.

I regret that I can offer no better solution aside from getting a fully supported plug-and-play device.
The problems, the driver and my answer are the same in both cases.

Here is another: [https://askubuntu.com/questions/939177/error-when-trying-to-install-drivers-for-tp-link-ac600-t2u/939237#939237](https://askubuntu.com/questions/939177/error-when-trying-to-install-drivers-for-tp-link-ac600-t2u/939237#939237)

---

### Post by time_racer on 2017-07-27
This means a a dead-end.... Thanks chili555 for your assistance

---

