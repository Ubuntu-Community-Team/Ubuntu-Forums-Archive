---
title: "ZTE MF622 Wireless Broadband with Three Network"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by forbzie22 on 2008-11-05
Hi,

Im having a few issues with the Wireless 3G broadband card from three (MF622). When inserting the USB card ubuntu 8.10 picks up the card fine. Networking applet reports that the connection is successful. However, im still unable to access the internet. I found the following script which i had to save to /etc/udev/filename.rules. This seems to work but internet access seems to be intermittent. I have to reboot ubuntu and wait about 10 minutes before the internet starts working again.

Ive read somewhere that because this modem has USB storage it defaults to a storage device first rather than a modem. I wanted to know a way of forcing ubuntu to connect to the internet straight away.

ACTION!="add", GOTO="ZTE_End"



# Is this the ZeroCD device?

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",

SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"



# Is this the actual modem?

SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",

SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"



LABEL="ZTE_ZeroCD"

# This is the ZeroCD part of the card, remove

# the usb_storage kernel module so

# it does not get treated like a storage device

RUN+="/usr/src/usb_modeswitch-0.9.2/usb_modeswitch -d 1 -v 0x19d2 -p 0x2000 -V 0x19d2 -P 0x0001" 



LABEL="ZTE_Modem"

# This is the Modem part of the card, let's

# load usbserial with the correct vendor

# and product ID's so we get our usb serial devices

RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",

# Make users belonging to the dialout group

# able to use the usb serial devices.

MODE="660", GROUP="dialout"



LABEL="ZTE_End"

Any suggestions would be helpful.

Thanks

---

