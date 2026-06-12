---
title: "TP-Link TL-WN725N nano wireless adapter not being recognized as a wireless device"
date: 2014-04-05
forum: Networking &amp; Wireless
---

### Post by aman207 on 2014-04-05
The default wireless card that came with my laptop is crap, so I bought a TP-LInk Nano USB Adapter with the model no TL-WN725N. Ubuntu doesn't recognize this device as a wireless one and I can't seem to find any drivers for or a package that has drivers. Might someone be able to point me to that package with the drivers? Thanks

---

### Post by chili555 on 2014-04-05
There are at least two different versions of this device. Let's see which you have. Please open a terminal and run and post:```
lsusb
```Thanks.

---

### Post by aman207 on 2014-04-05
> **chili555 said:**
> There are at least two different versions of this device. Let's see which you have. Please open a terminal and run and post:```
lsusb
```Thanks.
```
lsusb
``` returns this

```
Bus 001 Device 005: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Yes my device is plugged in and there is nothing else in the usb slots

---

### Post by chili555 on 2014-04-05
The solution depends on your Ubuntu version:```
lsb_release -d
uname -r
```This *may* work, depending on the results from above: [http://ubuntuforums.org/showthread.php?t=2172877&p=12781744#post12781744](http://ubuntuforums.org/showthread.php?t=2172877&p=12781744#post12781744)

---

### Post by aman207 on 2014-04-06
> **chili555 said:**
> The solution depends on your Ubuntu version:```
lsb_release -d
uname -r
```This *may* work, depending on the results from above: [http://ubuntuforums.org/showthread.php?t=2172877&p=12781744#post12781744](http://ubuntuforums.org/showthread.php?t=2172877&p=12781744#post12781744)

```
lsb_release -d
Description:    Ubuntu 12.04.4 LTS
uname -r
3.8.0-38-generic


```
Hm, no unfortunately that did not work for me.

---

### Post by chili555 on 2014-04-06
> **aman207 said:**
> Hm, no unfortunately that did not work for me.Not much to go on there. Did the driver not install because of an error? Was there an error when you modprobbed the driver? Did the driver load but you couldn't connect? Did you connect but the connection drops? Was there a kernel panic? Did your computer burst into flames? 

We might be able to help if we could hear some details and see the exact error.

---

