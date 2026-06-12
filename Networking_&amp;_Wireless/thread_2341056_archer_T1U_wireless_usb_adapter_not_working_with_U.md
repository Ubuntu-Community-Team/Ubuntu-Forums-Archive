---
title: "archer T1U wireless usb adapter not working with Ubuntu 16.04"
date: 2016-10-24
forum: Networking &amp; Wireless
---

### Post by boneywigs on 2016-10-24
Hello 

I am fairly new to Ubuntu but am studying computer science with the Open University.  I have recently bought a workstation which didn't come with a wireless card so I bought a TP-Link archer T1U which I am having trouble installing the driver.  The support from TP-Link said that they only support linux kernel 3.3 to 3.6 but my kernel is 4.4 and they don't support that.  They said about posting on forums to see if any one could help.   Any help would be appreciated on a compatible driver or an alternative dongle that would be ok with Ubuntu 16.04

Thanks

---

### Post by Geoffrey_Arndt on 2016-10-24
TP-Link made it a point to say they will not support Linux anymore:   However lf you prefer plug & Play for convenience . . . go here:    [http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by jeremy31 on 2016-10-25
Moved to networking
Please post results for ```
lsusb
``` with this wifi plugged in

---

### Post by susovimi on 2016-10-26
I have the same problem as him. When I put lsusb in a terminal I have:

```

suso@Susp-PC:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5710 IMC Networks UVC VGA Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1058:259f Western Digital Technologies, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 062a:5918 Creative Labs 
Bus 003 Device 004: ID 2357:0105  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

System does not detect the usb wifi

---

### Post by jeremy31 on 2016-10-26
I would try Pilot6's answer from [http://askubuntu.com/a/819231/300665](http://askubuntu.com/a/819231/300665)

---

### Post by goldendel on 2016-10-26
Yep.  Pilot6's answer worked for me too!

---

### Post by boneywigs on 2016-10-26
ok thanks guys I ended up getting a wifi booster that plugs into work station by Ethernet.  No help from TP Link so just took the thing back to the shop and got a refund.  Thanks for your help though guys.

---

