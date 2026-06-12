---
title: "RT3062 make not working"
date: 2015-10-01
forum: Networking &amp; Wireless
---

### Post by Kaijday on 2015-10-01
So i have an edimax ew 7711ln PCI card which i have never had any problem with. It's also working fine under windows.

I reinstall Arch, doesn't work. Install Ubuntu, doesnt work. I do a bit of reading and it turns out I may need to use RT3062 under Ubuntu. So using Camicri Cube server I install build-essentials and linux-headers and download the RALINK driver.

However when I run make I get:

```
scripts/Makefile.build:257: recipe for target '/home/kai/Desktop/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.o' failed
make[2]: *** [/home/kai/Desktop/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.o] Error 1
Makefile:1394: recipe for target '_module_/home/kai/Desktop/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux' failed
make[1]: *** [_module_/home/kai/Desktop/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-26-generic'
Makefile:244: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2


```

Any ideas?

---

### Post by chili555 on 2015-10-01
> [COLOR="#FF0000"]2010[/COLOR]_07_16_RT3062_Linux_STA_v2.4.0.0That creaky, moldy antique will never work and I suspect it is incorrect for your device anyway.

Please post:```
lsusb
```Thanks.

---

### Post by Kaijday on 2015-10-05
Sorry, after a few days of battling to get my mouse working I've logged into Ubuntu again and my wireless is working! Not a clue why.

I'll mark as solved :)

---

