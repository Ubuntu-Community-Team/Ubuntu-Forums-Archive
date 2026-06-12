---
title: "Laptop, trransfer wireless driver from Ubuntu 10.10 to 9.10"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by SG12010 on 2010-12-27
I have a laptop with Ubuntu 9.10 it works fine except for wireless.

Ubuntu 10.10 live cd, Lan and Wireless works fine, but when it is installed both Lan and Wireless fail.

Is there any way of transferring the wireless driver from Ubuntu 10.10 to 9.10.


Thanks SG1

---

### Post by Bucky Ball on 2010-12-27
You may find dependency problems.

---

### Post by marbertone on 2010-12-27
Hi,
try to figure out the file ```
 /etc/network/interfaces 
``` . In my case it is ```
 auto lo
iface lo inet loopback
iwconfig wlan0 power timeout 500ms
iface dsl-provider inet ppp
provider dsl-provider

```
network-manager and pppoeconf often get into mess.
Cheers,
Mario Alberto

---

