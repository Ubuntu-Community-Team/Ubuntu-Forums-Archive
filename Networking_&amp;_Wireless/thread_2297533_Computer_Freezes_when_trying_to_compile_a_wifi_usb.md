---
title: "Computer Freezes when trying to compile a wifi usb adapter driver"
date: 2015-10-04
forum: Networking &amp; Wireless
---

### Post by jrm-odier on 2015-10-04
Hello, 

I have a brand new ubuntu 14.04 installation.

I have a problem with my wifi adapter. 
It is a D-Link DWA 131, model E1.

It is not working (not a surprise considering the number of posts about it) so I tried to download the driver and compile it.

So i uncompress the file, go in it, and go for :

```
make
``` to compile it.
```
sudo insmod 8192eu.ko
```

and then everything freezes, the only way to escape it is to force shutdown the computer.
Afterward I have a nice desktop Bug (I have the same when I am installing unbuntu in the usb boot mode) where a black vertical bar reduce the resolution display at the right (3cm long). Then, if I want to shutdown, the computer shows the never ending ubuntu logo. So the only way for me is to reinstall ubuntu (4 times already? yes!)


I also used ```
modprobe
```. Same result

Thanks and good luck.

---

