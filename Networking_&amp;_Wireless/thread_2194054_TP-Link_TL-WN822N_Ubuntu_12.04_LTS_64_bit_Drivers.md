---
title: "TP-Link TL-WN822N Ubuntu 12.04 LTS 64 bit Drivers"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by hiteshhp on 2013-12-16
Hello Guys

Newbi on linux here. 
OS System: Ubuntu 12.04 LTS 64 bit 
Kernel: 3.8.0.29 generic
Wirelss USB adaptor : TP link TL-WN822N Version 3.0 (RTL8192cu)
I made wireless work using instructions at 

[http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html](http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html)

Now question is what should i do to preserve these drivers for future upgrade, i mean when i will upgrade Linux kernels will i lose wireless ? if yes, what should i do to preserve them.

Thanks 

Regards

Hitesh

---

### Post by chili555 on 2013-12-16
When a later kernel version is installed, after the required reboot, re-install the wireless driver:```
cd ~/Desktop/RTLwhatever  [COLOR="#FF0000"]<--or wherever you downloaded and extracted the driver file[/COLOR]
./install.sh
sudo modprobe rtl8192cu
```This driver file is getting pretty old. If it stops working as expected, there are other, probably better ways to install this driver. Post back at that time and we'll be happy to help. For now, there is no need to fix what isn't broken.

---

### Post by hiteshhp on 2013-12-16
Thanks chili555

---

