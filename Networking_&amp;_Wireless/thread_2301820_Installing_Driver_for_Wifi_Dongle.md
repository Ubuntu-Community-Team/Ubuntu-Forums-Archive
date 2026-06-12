---
title: "Installing Driver for Wifi Dongle"
date: 2015-11-05
forum: Networking &amp; Wireless
---

### Post by ohdavy on 2015-11-05
I recently installed Ubuntu and my wifi dongle will not work.  It's not a USB/Hardware issue since the the USB device still works through windows.  The website for my network adapter has drivers specifically for Linux, but my googling has not helped me figure out how to install them.  ([http://www.mybolse.com/m/support/Wireless/index.html](http://www.mybolse.com/m/support/Wireless/index.html) , N600 Wireless Adapter).  It shows up when I run the lsusb command as:

Bus 001 Device 006: ID 0bda:8194 Realtek Semiconductor Corp.

What should my next step be?

---

### Post by ohdavy on 2015-11-05
Sorry jumped the gun, I ran the 

sudo apt-get update
sudo apt-get dist-upgrade

and rebooted and that did not solve the issue.

I also ran the wireless info script.
[ATTACH=CONFIG]265383[/ATTACH]

---

### Post by jeremy31 on 2015-11-05
This should work for that after looking at the source code
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
sudo depmod -a
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
```

Reboot

---

