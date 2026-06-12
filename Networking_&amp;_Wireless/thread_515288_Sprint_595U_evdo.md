---
title: "Sprint 595U evdo"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by goneskiing on 2007-08-01
I'm trying to connect my Feisty to the Spring 595U usb modem.  I followed the WVDial instructions that worked on my previous pcmcia card.  I've tried to change the device/ttyACM0 to device/ttyUSB0 or 1 and still get "cannot open /dev/ttyUSB0: no such file or directory"

any ideas ?  thks.

---

### Post by goneskiing on 2007-08-02
Made some progress after using the following commands:
lsusb
sudo rmmod usbserial (gives error that /proc/ file is not there)
dmesg (which shows modem installed and vendor and product id)
sudo modprobe usbserial vendor=0x1199 product=0x0120

I then edited /etc/wvdial.conf to reflect /dev/ttyUSB0
after typing "wvdial"  modem now connects, shows ip and dns

But when I try to go to any website it just searches with no connection (green light flashes on modem).  This seems like some sort of handshaking or DNS problem - any suggestions ?   

Also modprobe only lasts for the session - where does it get listed to invoke at startup ?

---

