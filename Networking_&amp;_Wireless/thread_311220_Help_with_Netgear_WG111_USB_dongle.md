---
title: "Help with Netgear WG111 USB dongle"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by CloudANDTidus on 2006-12-02
Hey there, I'm in need of some help.

I recently installed Ubuntu 6.06 onto my desktop PC (its on the same HDD as a installation of Windows XP). The install process went dandy but I've kinda hit a wall as to getting online.

I'm using a Netgear WG111 v2 wireless dongle which obviously, only came with Windows drivers.

I'm (very) new to linux, and would really appreciate some guidance as to how I go about getting the dongle to work with Ubuntu.

Thanks in advance.

---

### Post by FrodoB on 2006-12-02
These devices, the Netgear WG111v2, either just work in Ubuntu 6.10 Edgy Elf or they cannot be made to work, except by ndiswrapper.

I am one of the fortunate folks who have one that just works.

To see if yours is going to work, do a fresh boot of your system and then plug the device in to a usb port and provide the outputs of the following:

lsusb

iwconfig

and the last part of the output of dmesg, which should be something like this:

[17242550.944000] Linux kernel driver for RTL8187 based WLAN cards
[17242550.944000] Copyright (c) 2004-2005, Andrea Merello
[17242550.944000] rtl8187: Initializing module
[17242550.944000] rtl8187: Wireless extensions version 20
[17242550.944000] rtl8187: Initializing proc filesystem
[17242550.948000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17242551.068000] rtl8187: Card MAC address is 00:14:6c:66:49:47
[17242551.248000] rtl8187: Card reports RF frontend Realtek 8225
[17242551.248000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17242551.248000] rtl8187: WW:use it with care and at your own risk and
[17242551.248000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17242551.284000] rtl8187: This seems a legacy 1st version radio
[17242551.284000] rtl8187: PAPE from CONFIG2: 0
[17242551.284000] rtl8187: Driver probe completed
[17242551.284000] 
[17242551.284000] usbcore: registered new driver rtl8187
[17242551.432000] rtl8187: Setting SW wep key
[17242552.116000] rtl8187: Card successfully reset

---

