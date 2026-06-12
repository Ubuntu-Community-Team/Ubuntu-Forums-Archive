---
title: "RTL8192EE wifi unstable pings, packet loss 14.04.1 &amp; 14.10 Lenovo e545"
date: 2014-12-08
forum: Networking &amp; Wireless
---

### Post by bathynomusBLUE on 2014-12-08
This wifi card seems to have a lot of trouble on Ubuntu 14.04.1 & 14.10 even with Kernel updates. I tried lots of different suggestions from these forums as well as other sites. The only one that worked for me was from the Arch Linux site and the commands worked perfectly on Ubuntu. My laptop is a Lenovo e545 (20B20011US). Perhaps someone can assist me in filing a bug report, if this has not been done already.

```
git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo modprobe -rv rtl8188ee
sudo make install
sudo modprobe -v rtl8188ee
```
reboot

Source: [https://bbs.archlinux.org/viewtopic.php?pid=1471267#p1471267](https://bbs.archlinux.org/viewtopic.php?pid=1471267#p1471267)

---

### Post by bathynomusBLUE on 2014-12-09
A note about this, sometimes suspend fails. So, if I close my laptop lid and open it again, the mouse is frozen with a black screen. I have to hard reset, unless someone has a workaround.

---

