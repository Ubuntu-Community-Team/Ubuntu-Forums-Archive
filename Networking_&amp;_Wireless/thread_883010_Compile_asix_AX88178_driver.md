---
title: "Compile asix AX88178 driver"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by digitalkarabao on 2008-08-07
Hello. I am using a USB to LAN adapter in my laptop running Ubuntu Gutsy after the onboard LAN card on my laptop stopped working. The USB to LAN adapter is a **PLANEX GU-1000T**. I believe the chipset is an **ASIX AX88178**. It loads the **usbnet **and **asix** modules when I plug it in but it fails to obtain an IP from DHCP. I read a lot and performed troubleshooting steps to isolate whether the issue is on the DHCP/networking config settings but nothing changes. My issue has the same symptoms as the guy from the thread:

[http://ubuntuforums.org/showthread.php?t=730205](http://ubuntuforums.org/showthread.php?t=730205) 

I suspect that it must be the driver. So,  I am hoping someone could walk me through on building and compiling the driver from the manufacturer's website below because I want to give it a try and see if it is different from the asix.ko module that comes with Gutsy. 

[http://www.asix.com.tw/download.php?sub=driverdetail&PItemID=84](http://www.asix.com.tw/download.php?sub=driverdetail&PItemID=84)

I am running the 2.6.22-14-generic kernel.

Help appreciated. Thanks a lot.

---

### Post by chili555 on 2008-08-07
After downloading the file AX88whatever.zip file to your desktop, right click it and select 'Extract here.' Drop your install CD in the tray. Open a terminal and do:```
sudo apt-cdrom -add
sudo apt-get install build-essential
sudo apt-get install linux-headers-generic
```Assuming all goes well to this point, do:```
cd ~/Desktop/AX88772_772A_LINUX2.6.14_REV105
make
sudo make install
```If this compiles, if you get an updated kernel, this new driver will not work! You will have compiled it against your 2.6.22-14-generic kernel and if you do an update, the in-built asix.ko will be in place.

I was not able to compile this against 2.6.24-19. Post back when you get stuck.

---

### Post by digitalkarabao on 2008-08-08
Thank you for responding man. I did this and the driver fails to compile returning a barrage of errors.  An excerpt I posted below.

```
/home/tungsten/AX88772/asix.c:1722: error: unknown field ‘status’ specified in initializer
/home/tungsten/AX88772/asix.c:1722: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1722: warning: (near initialization for ‘dlink_dub_e100b_info’)
/home/tungsten/AX88772/asix.c:1723: error: unknown field ‘link_reset’ specified in initializer
/home/tungsten/AX88772/asix.c:1723: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1723: warning: (near initialization for ‘dlink_dub_e100b_info’)
/home/tungsten/AX88772/asix.c:1724: error: unknown field ‘reset’ specified in initializer
/home/tungsten/AX88772/asix.c:1724: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1724: warning: (near initialization for ‘dlink_dub_e100b_info’)
/home/tungsten/AX88772/asix.c:1725: error: unknown field ‘flags’ specified in initializer
/home/tungsten/AX88772/asix.c:1725: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1725: warning: (near initialization for ‘dlink_dub_e100b_info’)
/home/tungsten/AX88772/asix.c:1726: error: unknown field ‘rx_fixup’ specified in initializer
/home/tungsten/AX88772/asix.c:1726: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1726: warning: (near initialization for ‘dlink_dub_e100b_info’)
/home/tungsten/AX88772/asix.c:1727: error: unknown field ‘tx_fixup’ specified in initializer
/home/tungsten/AX88772/asix.c:1727: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1727: warning: (near initialization for ‘dlink_dub_e100b_info’)
/home/tungsten/AX88772/asix.c:1728: error: unknown field ‘data’ specified in initializer
/home/tungsten/AX88772/asix.c:1728: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1728: warning: (near initialization for ‘dlink_dub_e100b_info’)
/home/tungsten/AX88772/asix.c:1731: error: variable ‘ax88772a_info’ has initializer but incomplete type
/home/tungsten/AX88772/asix.c:1732: error: unknown field ‘description’ specified in initializer
/home/tungsten/AX88772/asix.c:1732: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1732: warning: (near initialization for ‘ax88772a_info’)
/home/tungsten/AX88772/asix.c:1733: error: unknown field ‘bind’ specified in initializer
/home/tungsten/AX88772/asix.c:1733: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1733: warning: (near initialization for ‘ax88772a_info’)
/home/tungsten/AX88772/asix.c:1734: error: unknown field ‘status’ specified in initializer
/home/tungsten/AX88772/asix.c:1734: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1734: warning: (near initialization for ‘ax88772a_info’)
/home/tungsten/AX88772/asix.c:1735: error: unknown field ‘link_reset’ specified in initializer
/home/tungsten/AX88772/asix.c:1735: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1735: warning: (near initialization for ‘ax88772a_info’)
/home/tungsten/AX88772/asix.c:1736: error: unknown field ‘reset’ specified in initializer
/home/tungsten/AX88772/asix.c:1736: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1736: warning: (near initialization for ‘ax88772a_info’)
/home/tungsten/AX88772/asix.c:1737: error: unknown field ‘flags’ specified in initializer
/home/tungsten/AX88772/asix.c:1737: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1737: warning: (near initialization for ‘ax88772a_info’)
/home/tungsten/AX88772/asix.c:1738: error: unknown field ‘rx_fixup’ specified in initializer
/home/tungsten/AX88772/asix.c:1738: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1738: warning: (near initialization for ‘ax88772a_info’)
/home/tungsten/AX88772/asix.c:1739: error: unknown field ‘tx_fixup’ specified in initializer
/home/tungsten/AX88772/asix.c:1739: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1739: warning: (near initialization for ‘ax88772a_info’)
/home/tungsten/AX88772/asix.c:1740: error: unknown field ‘data’ specified in initializer
/home/tungsten/AX88772/asix.c:1740: warning: excess elements in struct initializer
/home/tungsten/AX88772/asix.c:1740: warning: (near initialization for ‘ax88772a_info’)
/home/tungsten/AX88772/asix.c:1837: error: ‘usbnet_probe’ undeclared here (not in a function)
/home/tungsten/AX88772/asix.c:1838: error: ‘usbnet_suspend’ undeclared here (not in a function)
/home/tungsten/AX88772/asix.c:1839: error: ‘usbnet_resume’ undeclared here (not in a function)
/home/tungsten/AX88772/asix.c:1840: error: ‘usbnet_disconnect’ undeclared here (not in a function)
make[2]: *** [/home/tungsten/AX88772/asix.o] Error 1
make[1]: *** [_module_/home/tungsten/AX88772] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

```

I guess I better try a Hardy Heron live CD and find out if my USB to LAN adapter works out of the box.

---

