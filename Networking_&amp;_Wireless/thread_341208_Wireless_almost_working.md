---
title: "Wireless almost working"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by boilermaker on 2007-01-18
Guys:


Right now i am able to see the LED for wireless card working..... But in the system device manager i am able to see the driver file to be bcm43xx. So what i did was rename the file (windows driver) to be bcm43xx and 'ndiswrapper' ed it.

Now when i start network manager it said starting interface application (loads to about 28%) and then fades out ](*,) 


Any tip would be greatly appreciated

---

### Post by evilghost on 2007-01-18
If you're using ndiswrapper you need to add bcm43xx to /etc/modprobe.d/blacklist

---

