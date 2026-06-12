---
title: "install e220 modem please help"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by NARINDER DHANOA on 2008-04-17
I am totally new to linux ubuntu ( 7.10 ) and having difficulty in setting up a e220 modem on the 3 network i would be totally grateful if anyone could assist me to get it working

---

### Post by ibutho on 2008-04-17
I've done this before (on openSUSE and Fedora). One option is to plugin your usb modem, switch on the computer and use something like kppp or gnome ppp to configure the modem and dialout. On my system the modem is given the device name /dev/ttyUSB0, the authentication type for 3 is chap, the dial out number is *99# and choose any user name and password you like (I just use the username "user" without a password).

---

### Post by NARINDER DHANOA on 2008-04-17
I am completely new to unbuntu operating system if anyone can assist step by step procedure it would be great below some one has recomended me to do this but still no joy 

[E220 Dialer]
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
Init5 = AT+CGDCONT=1, "IP","three.co.uk"; Modem Type = Analog Modem ISDN = 0 Phone = *99***1# Modem = /dev/ttyUSB0 Username = username Dial Command = ATDT Password = password Baud = 460800

Then, go to terminal and enter the following:

sudo rmmod usb-storage

sudo modprobe usbserial vendor=0x12d1 product=0x1003 sudo wvdial hsdpa


The command window will hang for a second then connect.

---

### Post by ibutho on 2008-04-18
Did you at least try to use kppp or gnomeppp or is that not what you were looking for?

---

