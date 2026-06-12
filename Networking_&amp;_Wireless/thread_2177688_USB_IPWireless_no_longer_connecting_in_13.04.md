---
title: "USB IPWireless no longer connecting in 13.04"
date: 2013-09-29
forum: Networking &amp; Wireless
---

### Post by trh79 on 2013-09-29
I have recently installed Kubuntu 13.04 32bit as a dual boot along side my older Kubuntu 10.
My only means of access to the internet has been a USB Woosh connection which uses an IPWireless device.
In the old Kubuntu install, the directions shown here [http://wiki.wlug.org.nz/WooshWireless](http://wiki.wlug.org.nz/WooshWireless) under "How to configure a Woosh modem using the USB cable under Linux"
allow me to connect.

Unfortunately in Kubuntu 13.04 I can't connect using this procedure and I'd love some help!


It seems it is failing early in the modem handshake, here are some relevant bits from the CLI:

lsusb
Bus 002 Device 004: ID 0bc3:0001 IPWireless, Inc. UMTS-TDD (TD-CDMA) modem

tail /var/log/syslog
Sep 30 12:48:10 trh-nix13 pppd[3669]: pppd 2.4.5 started by trh, uid 1000
Sep 30 12:48:10 trh-nix13 pppd[3669]: Removed stale lock on ttyUSB0 (pid 1906)
Sep 30 12:48:11 trh-nix13 chat[3671]: timeout set to 30 seconds
Sep 30 12:48:11 trh-nix13 chat[3671]: abort on (NO CARRIER)
Sep 30 12:48:11 trh-nix13 chat[3671]: abort on (BUSY)
Sep 30 12:48:11 trh-nix13 chat[3671]: send (^MAT^M)
Sep 30 12:48:11 trh-nix13 chat[3671]: expect (OK)
Sep 30 12:48:14 trh-nix13 chat[3648]: alarm
Sep 30 12:48:14 trh-nix13 chat[3648]: Failed

dmesg
[    2.080585] usb 2-1.3: New USB device found, idVendor=0bc3, idProduct=0001
[    2.080588] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.080591] usb 2-1.3: Product: IPWireless 3G Modem
[    2.080594] usb 2-1.3: Manufacturer: IPWireless, Inc.
[    2.080596] usb 2-1.3: SerialNumber: 352697000204245
[    2.150154] usb 2-1.4: new high-speed USB device number 5 using ehci-pci

[   11.711545] usbcore: registered new interface driver usbserial
[   11.711558] usbcore: registered new interface driver usbserial_generic
[   11.711570] usbserial: USB Serial support registered for generic
[   11.718737] usbcore: registered new interface driver ipw
[   11.718750] usbserial: USB Serial support registered for IPWireless converter
[   11.718763] ipw 2-1.3:1.0: IPWireless converter converter detected
[   11.718844] usb 2-1.3: IPWireless converter converter now attached to ttyUSB0
[   11.727817] tda829x 9-0042: type set to tda8295
[   11.759364] tda18271 9-0060: creating new instance
[   11.794006] TDA18271HD/C1 detected @ 9-0060
[   11.848322] init: failsafe main process (770) killed by TERM signal
[   12.668585] init: avahi-cups-reload main process (994) terminated with status 1
[   13.564904] r8169 0000:01:00.0 eth0: link down
[   13.564947] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.565301] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[26432.542480] usb 2-1.2: USB disconnect, device number 3

pppd debug call woosh
/var/log/ppp-connect-errors
Dialling w00sh...
Dialling w00sh...
Dialling w00sh...
Dialling w00sh...
Dialling w00sh...
Dialling w00sh...
Dialling w00sh...

 
Could anyone give me some advice of where to go next?

---

### Post by MIJ-VI on 2013-09-30
Possibly related (post #7):

[ubuntu] Realtek RTL8192CU Driver issues under 13.04
[http://ubuntuforums.org/showthread.php?t=2148130&p=12803070#post12803070](http://ubuntuforums.org/showthread.php?t=2148130&p=12803070#post12803070)

---

### Post by trh79 on 2013-10-01
FWIW I've tested this on Kubuntu 13.10 and 12.04 lts and I have the same issue.

---

### Post by MIJ-VI on 2013-10-01
Hmm... Start another thread / cast a wider net?

Linux - Networking - LinuxQuestions.org
[https://www.linuxquestions.org/questions/linux-networking-3/](https://www.linuxquestions.org/questions/linux-networking-3/)

---

