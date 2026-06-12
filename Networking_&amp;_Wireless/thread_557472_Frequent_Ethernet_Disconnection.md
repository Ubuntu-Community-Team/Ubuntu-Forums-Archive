---
title: "Frequent Ethernet Disconnection"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by simontay78 on 2007-09-22
ok so I am brand new to ubuntu fiesty. I had view all related post but can't seems to find solution! 

I have a AMD64 Desktop with fiesty 64bit with a 3Com 3c900B-TPO Ethernet card. I don't know if this is a supported card or not, 

The problem is **frequent Ethernet disconnection** while downloading big files using torrent or firefox. The connection speed for torrent is way way below....like 0.01kbps...when my broad band is 10mb subscription. 

this is the output of lspci -v | less

```
01:06.0 Ethernet controller: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone] (rev 04)
        Subsystem: 3Com Corporation 3C900B-TPO Etherlink XL TPO 10Mb
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at 7000 [size=128]
        Memory at f3006000 (32-bit, non-prefetchable) [size=128]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

```

I had ventured into the ndiswrapper but I cannot find my Ethernet Card listed...any help will be appreciated!! :)

Helpless Noob here!

---

### Post by finer recliner on 2007-09-22
dont rely on your torrent download speed as a measurment for your internet connection.

try this site: [http://www.speedtest.net/](http://www.speedtest.net/)

torrent speeds have many factors that can make them slow for reasons that have nothing to do with your own computer.

---

### Post by Dark Hornet on 2007-09-22
One other thing to consider--Comcast and some other cable providers have been "blocking" or "limiting" what they consider to be torrent traffic.

:guitar:

---

### Post by simontay78 on 2007-09-23
> **finer recliner said:**
> dont rely on your torrent download speed as a measurment for your internet connection.

try this site: [http://www.speedtest.net/](http://www.speedtest.net/)

torrent speeds have many factors that can make them slow for reasons that have nothing to do with your own computer.

My download using firefox (flock) is fantastic however it will be disconnected if it get overloaded!! not sure why...i got a feeling i need ndiswrapper or something...but not sure how to go about it...
[[IMG]http://www.speedtest.net/result/186862810.png[/IMG]](http://www.speedtest.net)

---

