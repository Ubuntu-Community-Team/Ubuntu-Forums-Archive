---
title: "How to configure 3G modem using CMD line on Ubuntu 14.04.1 LTS ARMv71"
date: 2015-02-10
forum: Networking &amp; Wireless
---

### Post by Charles_Seartech on 2015-02-10
I need to setup a 3G modem (LISA-U200 from uBlox) using the command line on a BeagleBone Black running Ubuntu 14.04.1 LTS (trusty) ARMv71.
I can connect the modem to a desktop running Ubuntu 14.10 (Utopic Unicorn) and using the GUI "Network Connections" "Add" setup the LISA-U200 USB modem and it works.
I have searched the web but don't seem to find the info required to setup the modem via the command line. 

Can someone point me in the right direction please?

The modem is detected on the BeagleBone:
ubuntu@arm:~$ lsusb
Bus 002 Device 005: ID 1546:1102 U-Blox AG


ubuntu@arm:~$ ls /sys/class/tty
...   ttyACM0  ttyACM1  ttyACM2  ttyACM3  ttyACM4  ttyACM5  ttyACM6  ...



ubuntu@arm:~$ ls /dev/serial/by-id/
usb-u-blox_u-blox_Wireless_Module_358901048269572-if00
usb-u-blox_u-blox_Wireless_Module_358901048269572-if02
usb-u-blox_u-blox_Wireless_Module_358901048269572-if04
usb-u-blox_u-blox_Wireless_Module_358901048269572-if06
usb-u-blox_u-blox_Wireless_Module_358901048269572-if08
usb-u-blox_u-blox_Wireless_Module_358901048269572-if0a
usb-u-blox_u-blox_Wireless_Module_358901048269572-if0c


ubuntu@arm:~$ ls /dev/serial/by-path/
platform-musb-hdrc.1.auto-usb-0:1.6:1.0
platform-musb-hdrc.1.auto-usb-0:1.6:1.10
platform-musb-hdrc.1.auto-usb-0:1.6:1.12
platform-musb-hdrc.1.auto-usb-0:1.6:1.2
platform-musb-hdrc.1.auto-usb-0:1.6:1.4
platform-musb-hdrc.1.auto-usb-0:1.6:1.6
platform-musb-hdrc.1.auto-usb-0:1.6:1.8


I just need to know if there is some kind of script I can run or if there is mechanism to emulate what the GUI does in the desktop version.

Thanks,
Charles

---

