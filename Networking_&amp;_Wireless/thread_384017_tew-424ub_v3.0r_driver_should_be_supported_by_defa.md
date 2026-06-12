---
title: "tew-424ub v3.0r driver should be supported by default"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by noodles12 on 2007-03-13
lsusb 

ID: Obda:8189 Realek Semiconductor corp. 


This should be supported by default in Ubuntu edgy. However is it not working. 


i check under //lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless 
and i find rtl8187 and rtl818x 


i do 

sudo modprobe rtl8187 and sudo modprobe rtl818x    and i get

FATAL: Module rtl8187 not found
FATAL: Module rtl818x not found

Please help. THank you.

---

### Post by saviles on 2007-03-15
I'm having a similar problem installing this device.

My question is here: [http://ubuntuforums.org/showthread.php?t=383504](http://ubuntuforums.org/showthread.php?t=383504)

Hopefully it can be helpful.

---

### Post by chili555 on 2007-03-15
Please try sudo modprobe r8187. When you see: ```
/lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/rtl8187
/lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/rtl8187/r8187.ko
```It is the .ko you want to modprobe, without the .ko. Who said linux was difficult?

---

### Post by noodles12 on 2007-03-16
I tried that and get the same message as before.

---

### Post by chili555 on 2007-03-16
Hmmm. Can't explain why, but sometimes sudo insmod works when sudo modprobe doesn't. Also, sometimes putting in the whole path does it: ```
sudo modprobe /lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/rtl8187/r8187.ko
```
Let us know.

---

### Post by noodles12 on 2007-03-16
modprobe with the whole path gets the same error. 

Using insmod with the whole path i get 

insmod: Error inserting. ""displays path here""   -l File exists.

---

