---
title: "Bigpond nextg wirless with usb desktop modem BP-EXT"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by sharke on 2007-08-25
The modem will not be recognised by the system and we need to fix

To use the usbserial driver we need to give the ID parammeters so in treminal without the modem connected.

lsusb
take note of installed devices

Connect modem
In terminal lsusb

Your modem will be now listed 
We now use those ids to connect via the usbserial module.

In terminal
sudo modprobe usbserial vendor=0x16d8 product=0x6280

Your modem will be attached to the usbserial module.

In terminal
dmesg
and we should see something like
[   35.400249] usbcore: registered new interface driver usbserial
[   35.400260] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   35.492923] usbserial_generic 1-1:1.0: generic converter detected
[   35.493085] usb 1-1: generic converter now attached to ttyUSB0
[   35.493092] usbserial_generic 1-1:1.1: generic converter detected
[   35.493131] usb 1-1: generic converter now attached to ttyUSB1
[   35.493137] usbserial_generic 1-1:1.2: generic converter detected
[   35.493173] usb 1-1: generic converter now attached to ttyUSB2
[   35.493182] usbcore: registered new interface driver usbserial_generic
[   35.493184] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core

Now to set up the connection
In terminal
sudo pppconfig

follow th onscreen instructions . As per the dmesg above your modem could be 1 of3 on my systam it is /dev/ttyUSB1

Once you have the connection setup you can connect
In terminak
pon ...... this is the name you gave your connection

happy surfing

We do have a network manager so we should use it so 
IN TERMINAL
sudo gedit /etc/network/lnterfaces
add
iface ppp0 inet ppp
provider ppp0

you can now connect and disconnect using network manager

Regards
Sharke

---

