---
title: "Marvell Technology Unknown device 4364"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by teomatto on 2007-01-09
hi all, i have bought an acer power m8. My problem is that i cannot see the ethernet device
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4364 (rev 12)

i have compiled and patched the new driver from marvell but nothing happens.

how can i solve this problem with dapper or edge ?

thanks for any help

matteo

---

### Post by teaker1s on 2007-01-09
could it just be module not loaded?

[COLOR="Red"]sudo modprobe nameofmodule[/COLOR]

---

### Post by teomatto on 2007-01-09
the module is load by the kernel
lsmod | grep sk
sk98lin               201812  0 
skge                   38672  0

thankyou

---

### Post by teomatto on 2007-01-11
hi all,
i solved installing a 2.6.19 kernel following this thread:
[http://www.ubuntuforums.org/showthread.php?t=326343](http://www.ubuntuforums.org/showthread.php?t=326343)

hope this help someone else
matteo:)

---

