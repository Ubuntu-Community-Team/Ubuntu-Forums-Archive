---
title: "D-link dwa-182 installation problem"
date: 2017-09-20
forum: Networking &amp; Wireless
---

### Post by blobber123 on 2017-09-20
Hi,

I come to you in need of aid with installing d-link dwa-182 usb wifi stick. I searched the forum and saw that there were some discussion about it, but unfortunately those did not help with my knowledge of ubuntu. 

I'm using 16.04 lts ubuntu and I went d-link website to get the linux drivers for the stick. I tried to use the install.sh to complete the installation, but all I got was bunch of errors. Could someone help me out? I attached the lsusb to here and some of the error messages which came up with install.sh. After this installation ubuntu does not recognize the stick at all. It can be seen with lsusb, but no wifi connection is made.

---

### Post by jeremy31 on 2017-09-20
*Thread moved to **Networking & Wireless**.*
Do you have another internet connection to this computer?  If so do
```
sudo apt-get install build-essential dkms git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_rtl8821AU_linux
sudo make -f Makefile.dkms install
```
Reboot

---

