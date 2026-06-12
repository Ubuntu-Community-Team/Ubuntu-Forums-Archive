---
title: "3G Modem Driver Problem (Need Help)"
date: 2015-06-26
forum: Networking &amp; Wireless
---

### Post by make-it-fast on 2015-06-26
Hello everyone! 

Recently I've got a new device: D-link DWP-157 wireless data modem 
[Here's some guide eng/ru]("http://ftp.dlink.ru/pub/usb/DWM-157/Description/D-Link%20DWM-157%20Linux%20guide.pdf")

I have a problem trying to go online (@ubuntu 14.04 x64): 
somehow drivers found inside this modem can not be installed properly, and I've found no any other driver for that model.

here's the result of "lsusb" and "dmesg" :

```
ub@ub:~$ lsusb
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 003: ID 0c45:670b Microdia 
[B]Bus 001 Device 006: ID 2001:7600 D-Link Corp. 
[/B]Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 1c4f:0032 SiGma Micro 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ub@ub:~$ dmesg | tail -20
[   89.871291] sr 2:0:0:1: Attached scsi generic sg3 type 5
[   89.879660] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   90.036478] usb 1-1.3: usbfs: interface 0 claimed by usb-storage while 'usb_modeswitch' sets config #2
[   90.054452] usb-storage 1-1.3:2.3: USB Mass Storage device detected
[   90.054591] scsi3 : usb-storage 1-1.3:2.3
[   90.054768] usb_modeswitch[2171]: segfault at 100000002 ip 00007fcfb67d5e0c sp 00007ffec3a97208 error 4 in libc-2.19.so[7fcfb6753000+1bb000]
[   90.385656] systemd-udevd[2148]: Failed to apply ACL on /dev/sr1: No such file or directory
[   90.385665] systemd-udevd[2148]: Failed to apply ACL on /dev/sr1: No such file or directory
[   90.396558] systemd-udevd[2141]: Failed to apply ACL on /dev/sr1: No such file or directory
[   90.396567] systemd-udevd[2141]: Failed to apply ACL on /dev/sr1: No such file or directory
[   91.130967] usb 1-1.3: reset high-speed USB device number 6 using ehci-pci
[   91.232520] scsi 3:0:0:0: Direct-Access     D-LINK   MicroSD Card     2.31 PQ: 0 ANSI: 2
[   91.234848] scsi 3:0:0:1: CD-ROM            D-LINK   CD-ROM           2.31 PQ: 0 ANSI: 2
[   91.235257] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   91.253257] sr1: scsi-1 drive
[   91.253406] sr 3:0:0:1: Attached scsi CD-ROM sr1
[   91.253480] sr 3:0:0:1: Attached scsi generic sg3 type 5
[   91.280393] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   91.585637] ISO 9660 Extensions: Microsoft Joliet Level 3
[   91.627607] ISO 9660 Extensions: RRIP_1991A

```

here we can see "usb_modeswitch" error, but, the problem is: drivers are there at the storage device, but installing them makes a mess. just look at the readme file and folders content @ screenshots attached

[ATTACH=CONFIG]262860[/ATTACH][ATTACH=CONFIG]262861[/ATTACH]

Readme:

```
1. copy LinuxModemShell to local
2. in local LinuxModemShell, install driver
   sudo sh install.sh
3. reboot the system after doing
   sudo sh bin/RemoveModemManager.sh     
4. sudo rmmod usbserial
5. in local LinuxModemShell, dial-up 
   sudo sh bin/linux-dialup.sh
```

1. i consider **"local"** means /usr/local/ so i put it over there..
2. 3. reboot goes fine 
4. **"sudo rmmod usbserial"** doesn't work... output : ```
 rmmod: ERROR: Module usbserial is not currently loaded

```
5. whatever, i run **"sudo sh bin/linux-dialup.sh" **and get ```
pppd: no process found
/usr/sbin/pppd: In file /etc/ppp/peers/linux_dial: unrecognized option '/dev/ttyUSB_sprd_modem'

```

by the way, inside **linux-dialup.sh **we see
```
#!/bin/bash

killall pppd
sleep 5 && /usr/sbin/pppd debug call linux_dial

```
....

that's it! i don't know if that matters, but at the moment i'm using my mobile as usb-modem, however it's found like "ethernet".. i mean maybe i should run everything offline or smthng...

THANKS for any help, i need to work and this problem is really killing me, considering that my previous modem just found dead 2 days ago......

p.s. should i post same question @ ask.ubuntu or not ? how does the system work :)

---

### Post by Lars Melin on 2015-10-05
Please paste the output from lsusb -v -d 2001:7600

---

### Post by kirahulsharan on 2016-07-27
D-vender : D-product  2001:7600
Dlink dongle DWP-157
how to modswitch
---------------------------------------------------------------
Look for target devices ...
   product ID matched
 Found devices in target mode or class (1)
Look for default devices ...
   product ID matched
 Found devices in default mode (1)
Access device 004 on bus 005
Get the current device configuration ...
 OK, got current device configuration (1)
Use interface number 0
Ambiguous Class/InterfaceClass: 0xef/0x08
Use endpoints 0x01 (out) and 0x81 (in)
Inquire device details; driver will be detached ...
Looking for active driver ...
 OK, driver detached


SCSI inquiry data (for identification)
-------------------------
  Vendor String: SPRD
   Model String: MicroSD Card
Revision String: 2.31
-------------------------


USB description data (for identification)
-------------------------
Manufacturer: Spreadtrum
     Product: SC7702 HSPA+ Datacard
  Serial No.: A734C5281BDF0E6
-------------------------
Warning: no switching method given. See documentation
-> Run lsusb to note any changes. Bye!


-----------------------------------------------------------------------
still not creating  serial port

---

### Post by jeremy31 on 2016-07-27
Can you use file manager to unmounted the device?

---

