---
title: "USB sis163u wifi help"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by mrsudo on 2007-11-15
i have a tew-424ub from trendnet which im trying to configure. 
i've gotten ndiswrapper installed and same with the driver (sis163u.inf and the corresponding .sys file)  

kevin@a1600n:~$ ndiswrapper -l
sis163u : driver installed
device (0457:0163) present

kevin@a1600n:~$ lsusb
Bus 002 Device 006: ID 0457:0163 Silicon Integrated Systems Corp.

kevin@a1600n:~$ iwlist wlan0 scan
wlan0 Interface doesn't support scanning.

kevin@a1600n:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.

kevin@a1600n:~$ lsmod | grep ndiswrapper

ndiswrapper 233632 0

usbcore 161584 10 ndiswrapper,gspca,sn9c102,xpad,usb_storage,usbhid, libusual,ohci_hcd,ehci_hcd


do i need to blacklist a particular driver? is the device disabled?  i have followed every tutorial on the subject ive found with no luck.  already edited /etc/network/interfaces.  even reinstalled ubuntu alltogether.  nothing

---

### Post by mrsudo on 2007-11-15
anyone? :(

---

