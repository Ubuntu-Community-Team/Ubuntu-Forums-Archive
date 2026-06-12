---
title: "Tried Everything ...wireless problems"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by SOG420 on 2007-05-01
I have tried installing several drivers with ndiswrapper and still can't get it to work. I feel like I've tried everything. iwconfig results in no wlan connection. Any help or referall would be helpful

 HP Pavilion dv2000
AMD turion 64
Broadcom  Corp : Unknown device  4311

---

### Post by MilosDusan on 2007-05-01
I had major issues getting Ubuntu to work with my WiFi adapter..

Have you tried ndiswrapper yet with the original install software for your WiFi adapter?  What steps have you taken so far?

And if all else fails, do what I did.. Go buy an Ubuntu supported WiFi adapter.. I know it may be a last resort, but I tell you this, I purchased a Linksys WMP54GV4 WiFi adapter, and I put it in the system, and it was like pure gold.. Plug and play right out of the box.. *sniff* .. almost brings a tear to my eye..

---

### Post by MilosDusan on 2007-05-01
Another thing you might try.. Sometimes ndiswrapper conflicts with the open source bcm43xx driver, and wont allow the actual driver to work properly.. Type the following in console to blacklist the driver.. 

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

---

