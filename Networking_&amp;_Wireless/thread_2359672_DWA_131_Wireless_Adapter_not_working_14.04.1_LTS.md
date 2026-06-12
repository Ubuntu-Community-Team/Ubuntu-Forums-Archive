---
title: "DWA 131 Wireless Adapter not working 14.04.1 LTS"
date: 2017-04-26
forum: Networking &amp; Wireless
---

### Post by hmsvigle on 2017-04-26
Hi All,

Please help me in troubleshooting the issue with my wireless USB adapter. 

OS                     - Ubbuntu 14.04.1 LTS
Wireless adapter - DWA 131 nano USB adapter, HW Version - E1.

Issue:- USB stick is getting detected. I have installed below driver. But the issue still persists. Please find the screenshots to understand my current configuration...

----------

```
himansu@himansu-Inspiron-5537:~/Desktop/DWA/Win7x86$ lsusb
Bus 001 Device 006: ID 0c45:64ad Microdia 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 04f3:0042 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 007: ID 1058:0839 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 2001:3319 D-Link Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


-------------------------------------------------------------------------------------------------------------------------------

I added a driver for this adapter to PPA. I have verified the inf file(driver package for Windows) and found the driver (rtl8192eu) is correct. 
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms
-------------------------------------------------------------------------------------------------------------------------------

Followed below steps also
```
sudo apt-get install git
git clone [https://github.com/Mange/rtl8192eu-linux-driver.git](https://github.com/Mange/rtl8192eu-linux-driver.git)
cd rtl8192eu-linux-driver
make
sudo make install
sudo modprobe 8192eu
```

-------------------------------------------------------------------------------------------------------------------------------

Following all the steps in the following link as well.

[http://bernaerts.dyndns.org/linux/74-ubuntu/277-ubuntu-precise-dwa-131-rev-b1](http://bernaerts.dyndns.org/linux/74-ubuntu/277-ubuntu-precise-dwa-131-rev-b1)

-------------------------------------------------------------------------------------------------------------------------------

I was following steps mentioned in following link.. I am getting "Invalid driver!" message as mentioned below. 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

```
himansu@himansu-Inspiron-5537:~/Desktop/DWA/Win81x86$ sudo ndiswrapper -i Dnetrtwlanu.inf 
driver dnetrtwlanu is already installed
himansu@himansu-Inspiron-5537:~/Desktop/DWA/Win81x86$ sudo ndiswrapper -l
[COLOR=#ff0000]dnetrtwlanu : invalid driver!
```
-------------------------------------------------------------------------------------------------------------------------------

I have received the driver for Linux from below link.
 
[http://files.dlink.com.au/Products/DWA-131/REV_E/Drivers/DWA-131_Linux_driver_v4.3.1.1.zip](http://files.dlink.com.au/Products/DWA-131/REV_E/Drivers/DWA-131_Linux_driver_v4.3.1.1.zip)

Kindly help me install the driver...

Please help me troubleshoot & fix the issue. I am suffering since a week now. Please help me out.

Thanks 
Himansu

---

### Post by slickymaster on 2017-04-26
*Thread moved to **Networking & Wireless*** and code tags added

---

### Post by hmsvigle on 2017-04-29
Hi All,

Please help me out in this. 

I referred following link. As per this, If i disable secure boot, that should resolve the issue. As i have the correct driver installed. 
Even the USB dlink 131 is working occassionally. However I face frequent disconnection. if the connection established, that doesnt last more than an hr. 

[https://askubuntu.com/questions/792773/dlink-dwa-131-h-w-ver-e1-f-w-ver-5-1-how-do-i-install-its-wifi-driver-in-ubu/792779#792779](https://askubuntu.com/questions/792773/dlink-dwa-131-h-w-ver-e1-f-w-ver-5-1-how-do-i-install-its-wifi-driver-in-ubu/792779#792779)


Please help me out...

---

