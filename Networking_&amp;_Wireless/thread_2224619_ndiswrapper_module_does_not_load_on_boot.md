---
title: "ndiswrapper module does not load on boot"
date: 2014-05-17
forum: Networking &amp; Wireless
---

### Post by DhrSchap on 2014-05-17
Hi
My Belkin F7d4101 v1 wifi dongle [broadcom BCM 4323] does not work out of the box on xubuntu 12.04 neither on my current version 14.04. I therefore downloaded and installed ndiswrapper 1.59 from the sourceforge as per the included instructions. The connection is working. However, it does not load on boot so I have to run ```
sudo modprobe ndiswrapper
```. I have added ndiswrapper to /etc/modules

Any suggestions ?

Thanks

JP

---

### Post by praseodym on 2014-05-18
Did you run
```

sudo ndiswrapper -ma
```

---

### Post by DhrSchap on 2014-05-18
solved - thanks:P

indeed I had only done 

```
 sudo ndiswrapper -m 
``` ommitting the a ```
 -ma 
```
 now it works

However when I look in /etc/modprobe.d/ndiswrapper.conf this file has 3 lines 

```

alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper

```


with only the middle one referring to my USB dongle as established with

```
 sudo ndiswrapper -l

bcmwlhigh5 : driver installed
    device (050D:615A) present

```


Can I safely delete those two other lines?

---

### Post by praseodym on 2014-05-18
It doesn&#8217;t matter, these lines refer to other devices

---

