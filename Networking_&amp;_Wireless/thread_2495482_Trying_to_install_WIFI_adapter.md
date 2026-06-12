---
title: "Trying to install WIFI adapter"
date: 2024-02-20
forum: Networking &amp; Wireless
---

### Post by bkz81 on 2024-02-20
Anyone have experience with trying to get this adapter to work under 22.04?  Bus 001 Device 003: ID 0bda:8832 Realtek Semiconductor Corp. 802.11ax WLAN Adapter 
"WAVLINK AX1800 WiFi 6 USB Adapter for PC, Dual Band Wireless USB Network Adapter for Desktop Laptop, 5GHz & 2.4GHz, MU-MIMO, 802.11ax"

[https://pastebin.com/EY6BWxYu](https://pastebin.com/EY6BWxYu)

---

### Post by jeremy31 on 2024-02-20
```
sudo apt install git dkms
git clone https://github.com/lwfinger/rtl8852au.git
sudo dkms add ./rtl8852au
sudo dkms install rtl8852au -v 1.15.0.1
```

Reboot

---

### Post by bkz81 on 2024-02-20
Thanks for the reply on this.   I got the following below after trying the first command.  

sudo apt install git dkms
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
dkms is already the newest version (2.8.7-2ubuntu2.2).
git is already the newest version (1:2.34.1-1ubuntu1.10).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu2) ...
Removing old rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
Deleting module rtl8812au-4.3.8.12175.20140902+dfsg completely from the DKMS tree.
Loading new rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
Building for 6.5.0-18-generic
Building initial module for 6.5.0-18-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/rtl8812au-dkms.0.crash'
Error! Bad return status for module build on kernel: 6.5.0-18-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log for more information.
dpkg: error processing package rtl8812au-dkms (--configure):
 installed rtl8812au-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 rtl8812au-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jeremy31 on 2024-02-20
Try ```
sudo apt remove rtl8812au-dkms
```

---

