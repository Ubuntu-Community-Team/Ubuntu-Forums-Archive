---
title: "Can't get a RTL8191SU Wlan dongle working"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by Nickjallday on 2014-08-13
[COLOR=#000000][FONT=Verdana]No this is for a PCDuino running ubuntu. So here's what I've done today with no dice.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I installed PCduino-linux-headers-3.4.79+[/FONT][/COLOR]

[COLOR=#666666][FONT=Verdana]**Code: [Select]**[/FONT][/COLOR]
wget [ftp://WebUser:Lc9FuH5r@23.251.207.30/cn/wlan/RTL819xSU_usb_linux_v2.6.6.0.20120405.zip](ftp://WebUser:Lc9FuH5r@23.251.207.30/cn/wlan/RTL819xSU_usb_linux_v2.6.6.0.20120405.zip)
cd Downloads
unzip RTL819xSU_usb_linux_v2.6.6.0.20120405.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver
tar -xzvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
sudo su
make

[COLOR=#000000][FONT=Verdana]Then I get an error. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]make ARCH=armv7l CROSS_COMPILE= -C /lib/modules/3.4.29+/build M=/home/ubuntu/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make: *** /lib/modules/3.4.29+/build: No such file or directory.  Stop.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make: *** [modules] Error 2[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Then I try.[/FONT][/COLOR]

[COLOR=#666666][FONT=Verdana]**Code: [Select]**[/FONT][/COLOR]
cd /lib/modules/3.4.29+/
mkdir build
cd /home/ubuntu/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
make

[COLOR=#000000][FONT=Verdana]Then I get. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]make ARCH=armv7l CROSS_COMPILE= -C /lib/modules/3.4.29+/build M=/home/ubuntu/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make[1]: Entering directory `/lib/modules/3.4.29+/build'[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make[1]: *** No rule to make target `modules'.  Stop.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make[1]: Leaving directory `/lib/modules/3.4.29+/build'[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make: *** [modules] Error 2[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have no clue how to make this dang thing work should I get order the recommended dongle?

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Other info:[/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana]**Code: [Select]**[/FONT][/COLOR]
lsusb
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 003: ID 0d8c:0103 C-Media Electronics, Inc. CM102-A+/102S+ Audio Controller
Bus 001 Device 004: ID 046d:0825 Logitech, Inc. Webcam C270
iwconfig
lo        no wireless extensions.
usb0      no wireless extensions.
tunl0     no wireless extensions.
sit0      no wireless extensions.
eth0      no wireless extensions.[COLOR=#000000][FONT=Verdana]
I've tried a few other guides on this forum other the course of the last three days and I still am at the same place I started at. Can anyone help? Thank you![/FONT][/COLOR]

---

### Post by Hadaka on 2014-08-13
Hi, this should get you going.
[http://ubuntuforums.org/showthread.php?t=1674994](http://ubuntuforums.org/showthread.php?t=1674994)
you might want to remove that directory you built.

---

