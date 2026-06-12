---
title: "USB wifi adapter not found"
date: 2018-11-22
forum: Networking &amp; Wireless
---

### Post by ankur.walia on 2018-11-22
have freshly installed ubuntu 18.04.1 LTS. My usb wifi adapter which  works perfectly fine in windows 10 in the same system (dual boot), is  not recognized here.  
I have gone through various posts here to identify but could not find anything to work.

the chip is a Realtek 8811AU/8812AU

log file - [http://paste.ubuntu.com/p/ZPhd97zK5X/](http://paste.ubuntu.com/p/ZPhd97zK5X/)

---

### Post by jeremy31 on 2018-11-23
Do in terminal
```
sudo apt install git dkms build-essential
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
```

Reboot

---

