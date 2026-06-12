---
title: "driver for sitecom wifi usb adapter N300"
date: 2014-09-21
forum: Networking &amp; Wireless
---

### Post by rubens3 on 2014-09-21
I am using ubuntu 12.01 lts with dual boot windows 7 on 64 bits Dell laptop.

I purchased sitecom wifi usb adapter N300 and it came with a install CD, working perfect on windows now.

Now I like to use this wifi adapter with ubuntu, but have no driver for ubuntu/linux on the install CD.

How to get a driver for this USB adapter to install in ubuntu 12.01??

---

### Post by praseodym on 2014-09-21
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

### Post by rubens3 on 2014-09-23
The adapter is working but it seems slower than when used with windows(and correct driver)
How can I check the speed of this driver and how to get the drivers name that ubuntu 12.04 uses?

Is using the "windows driver" via ndiswrapper an option to improve speed?

peter@peter-Inspiron-1750:~$ uname -a
Linux peter-Inspiron-1750 3.2.0-69-generic #103-Ubuntu SMP Tue Sep 2 05:02:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
peter@peter-Inspiron-1750:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:6400 Microdia 
Bus 002 Device 003: ID 0df6:0077 Sitecom Europe B.V. 
Bus 006 Device 002: ID 177f:1450 Sweex 
peter@peter-Inspiron-1750:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11abg  ESSID:"Ziggo28383_EXT"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 641:A3:205:22   
          Retry  long limit:7   RTS thr 0ff   Fragment thr off
          Power Managementff
          
wlan1     IEEE 802.11bgn  ESSID:"Ziggo28383_EXT"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 641:A3:205:22   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr off
          Power Management off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:294   Missed beacon:0

eth0      no wireless extensions.

peter@peter-Inspiron-1750:~$

---

### Post by praseodym on 2014-09-23
Change the driver via:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

