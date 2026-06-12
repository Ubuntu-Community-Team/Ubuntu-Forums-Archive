---
title: "4G/LTE USB not connecting to internet (4.9 kernel)"
date: 2017-06-22
forum: Networking &amp; Wireless
---

### Post by mavik30 on 2017-06-22
Hello,

Verizon U620L 4G/LTE able to connect inter net on 3.10.x kernel Ubuntu 16.04. Using following setup.

```
sudo pluma /etc/udev/rules.d/99-vzw_u620l.rules
SUBSYSTEM=="usb", ATTR{idVendor}=="1410", ATTR{idProduct}=="9020", ATTR{bConfigurationValue}=="1", ATTR{bConfigurationValue}="2"
```
```
sudo usb_modeswitch &#8211;v 0x1410 &#8211;p 0x9020 &#8211;u 4
```

On Kernel 4.9 with same setting above is not connecting to internet. Errors attach, Any changes needed to connect internet.
[ATTACH=CONFIG]275729[/ATTACH]


Thanks,
Answers Appreciated

---

### Post by jeremy31 on 2017-06-22
How did you get the 3.10 kernel on Ubuntu 16.04?  Why are you using the 4.9 kernel as it isn't supported?

Are you using the Verizon instructions from [https://www.verizonwireless.com/dam/support/pdf/user_guide/u620-linux-integration-guide-7-17-15.pdf](https://www.verizonwireless.com/dam/support/pdf/user_guide/u620-linux-integration-guide-7-17-15.pdf)

---

### Post by mavik30 on 2017-06-22
Thanks for replay,

This image Ubuntu 16.04 is for Odroid XU4 with different kernels 3.10.xx, and 4.9.xx

[http://odroid.com/dokuwiki/doku.php?id=en:xu3_release_linux_ubuntu](http://odroid.com/dokuwiki/doku.php?id=en:xu3_release_linux_ubuntu) -> 3.10.xx images

[http://odroid.com/dokuwiki/doku.php?id=en:xu3_ubuntu_k49_release_note_20170510](http://odroid.com/dokuwiki/doku.php?id=en:xu3_ubuntu_k49_release_note_20170510) -4.9 images

Yes, i Followed that pdf 3 chapter "Enumerating CDC- ECM + Modem Interfaces"

Internet worked perfectly on 3.10.xx kernel for a years or so.

Now few weeks back, Odroid has released new XU4Q that best supports 4.9 kernel and planed to upgrade kernel to 4.9.

Really fast and good performance, our app run better on 4.9 than on 3.10.xx,

Why it is not connecting to internet on 4.9 kernel with above settings. Any thing need to add.

---

### Post by mavik30 on 2017-06-25
Anything is needed for 4.9 kernel to work internet.

---

