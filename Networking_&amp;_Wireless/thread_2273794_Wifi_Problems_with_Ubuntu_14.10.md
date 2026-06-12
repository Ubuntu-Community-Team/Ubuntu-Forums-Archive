---
title: "Wifi Problems with Ubuntu 14.10"
date: 2015-04-15
forum: Networking &amp; Wireless
---

### Post by kim15 on 2015-04-15
My wifi slows down and stops to a halt every time I open Firefox to browse.  I mainly go on Youtube, Reddit. Tumblr... etc.  It will be just fine at first, but then suddenly it will slow then stop all together.  Youtube has the most problems.  I can barely watch one video.  The wifi usually goes back to normal once I turn it off for a few seconds and turn it back on, but as you can imagine it gets super irritating having to do it every five minutes or so.  I just switched from Windows 8.1 and I use a Lenovo G50-45 laptop.

---

### Post by Vladlenin5000 on 2015-04-15
Hi and welcome.

Pleased read the stickies in this section, especially the one that says ["Before posting in Networking & Wireless"]("http://ubuntuforums.org/showthread.php?t=370108").
Without additional info I can only suspect it has something to do with the AMD APU, because similar hardware often requires the AMD proprietary drivers for better performance (the Catalyst package isn't only for graphics).

---

### Post by kim15 on 2015-04-15
Well here's my wireless info if this helps at all.

---

### Post by Vladlenin5000 on 2015-04-15
Thank you and it certainly does help.

1. First things first, always use WPA2-AES (not WPA/WPA2 mixed mode), everything else is bad in one way or another.
2. Although changing the network settings as in 1) might just do it, it's also true your hardware is very new...

```
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be
```

This device may need a different (newer) driver. [This]("http://ubuntuforums.org/search.php?searchid=7423141") is what comes up by searching this forum alone.

---

### Post by jeremy31 on 2015-04-15
> **Vladlenin5000 said:**
> Thank you and it certainly does help.

1. First things first, always use WPA2-AES (not WPA/WPA2 mixed mode), everything else is bad in one way or another.
2. Although changing the network settings as in 1) might just do it, it's also true your hardware is very new...

```
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be
```

This device may need a different (newer) driver. [This]("http://ubuntuforums.org/search.php?searchid=7423141") is what comes up by searching this forum alone.

The search link came up empty for me, so

First try ```
echo "[COLOR=#6A6A6A][FONT=arial]**options rtl8723be**[/FONT][/COLOR][COLOR=#545454][FONT=arial] fwlps=0 swlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

[/FONT][/COLOR]Reboot and if that doesn't help then install backports

```
sudo apt-get install linux-headers-generic build-essential 
```
```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.gz
```
```
tar -zxvf backports-3.19-rc1-1.tar.gz
```
```
cd backports-3.19-rc1-1
```
```
make defconfig-rtlwifi
```
```
make
```
```
sudo make install
```


Reboot

---

### Post by kim15 on 2015-04-16
Thank you so much!  This seemed to work!

---

