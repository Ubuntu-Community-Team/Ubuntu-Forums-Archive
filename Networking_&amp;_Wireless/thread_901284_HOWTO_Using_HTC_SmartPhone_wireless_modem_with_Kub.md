---
title: "HOWTO: Using HTC SmartPhone wireless modem with Kubuntu/Ubuntu"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by lcorbeil on 2008-08-26
After a few hours of headaches, I've sucessfully used my HTC phone as a wireless modem with kubuntu 7.10 (should be same with Ubuntu).

Follow these steps to get it working (tough mine is a HTC S720, should work as well on other models):

(Dependencies: wvdial command and ipaq kernel modules)

1- Plug your HTC using usb cable to your computer
2- Make sure your data connection is closed and then run the wireless modem program
3- Start the connection (Menu/Start) on your PDA
4- Now, on your linux, type in bash "lsusb" (without quotes) and you should see something like this:

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 003: ID 0bb4:0b03 High Tech Computer Corp.
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp.
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Find out your HTC device in the list (mines High Tech Computer Corp.). You will need to get the vendor and product ids, identified by the ID 0bb4:0b03 just before your device's name. The first one if the vendor id (0bb4 or 0x0bb4) and the second one is the product id (0b03 or 0x0b03).

5- Once you get the product and vendor ids, you need to load the ipaq kernel module, pointed to the HTC using this command:

sudo modprobe ipaq vendor=0x0bb4 product=0x0b03

Just replace the vendor and product ids with yours, but don't forget the 0x before them.

To make sure the ipaq is loaded correctly, type dmesg and you should see something like this:

[ 2290.820000] usb 5-1: new full speed USB device using uhci_hcd and address 4
[ 2290.992000] usb 5-1: configuration #1 chosen from 1 choice
[ 2656.256000] usbcore: registered new interface driver usbserial
[ 2656.256000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 2656.256000] usbcore: registered new interface driver usbserial_generic
[ 2656.256000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 2656.268000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
[ 2656.268000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
[ 2656.268000] ipaq 5-1:1.0: PocketPC PDA converter detected
[ 2656.268000] usb 5-1: PocketPC PDA converter now attached to ttyUSB0
[ 2656.268000] ipaq 5-1:1.1: PocketPC PDA converter detected
[ 2656.272000] usb 5-1: PocketPC PDA converter now attached to ttyUSB1
[ 2656.272000] usbcore: registered new interface driver ipaq

Your modem is now available using the ttyUSB0 device.

6- Use wvdial to start a session using PPPd.

Here's an example of the wvdial.conf file (in /etc)

[Dialer Defaults]
Modem = /dev/ttyUSB0
Phone = #777
New PPPD = yes
Baud = 460800
Stupid Mode = 1
ISDN = 0
Auto DNS = 1
Username = yourphone
Password = none

you can copy paste this sample, and put your username and password as well as the correct phone number (call your provider for these information).

Invoke wvdial like this:

sudo wvdial

Your internet is ready on your computer using your HTC as a wireless modem.

NOTE: Keep in mind that you will need to load the ipaq module everytime you start your computer and want to use the wireless modem. Just make a small bash script for step 5 and 6. Your device vendor and product ids always stay the same, they are hardcoded in your device memory. Once you get them, hardcode them in your bash script.

Telus Mobility users
--------------------
As long as I know, no username and password are required for this provider, just put in your phone number and anything you want for the password.

---

