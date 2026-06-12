---
title: "Kernel upgrade disables WiFi"
date: 2018-08-09
forum: Networking &amp; Wireless
---

### Post by jet-bundle on 2018-08-09
I have an HP Paviliion TS11 running Lubuntu 16.04, with a dongle for WiFi access (I couldn't get the built-in RT3290 to work). The software for the dongle (rtl8812au) was installed using the help I received in [https://ubuntuforums.org/showthread.php?t=2368422](https://ubuntuforums.org/showthread.php?t=2368422). Now, though, after the most recent kernel upgade to 4.15.0-29, wifi has stopped working, though if I boot into 4.13.0-45 then everything is OK. This is the first time that a kernel upgrade has caused a problem (I started with 4.4.0-91).

 I'd be grateful for any advice on how to fix this.

---

### Post by chili555 on 2018-08-09
May we have a look at:```
sudo dkms status
```Thanks.

---

### Post by ajgreeny on 2018-08-09
Can you check that you have the header packages for kernel version 4.15.0-29; depending on how you moved to the 4.15 kernel series they may not have been installed by default.

Kernel version 4.15.0-30 arrived for me yesterday; if it's also in your repos try installing that and see if it helps.

---

### Post by jeremy31 on 2018-08-09
I never updated that for 4.15, do 
```
sudo dkms remove rtl8812AU/5 --all
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
```
Reboot

---

### Post by jet-bundle on 2018-08-10
Thanks to all who replied. I now have 4.15.0-30 with working WiFi, after having followed followed the instructions given by jeremy31 and carried out a software update.

---

