---
title: "problem to configure wireless modeam in ubuntu 7.10"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by manickam on 2008-05-08
hai 
    my name is manickam from india i have reliance wireless modeam (reliance is india net provider)but they did't give me linux modeam driver so that i can't configure in ubuntu 7.10 i need a solution for this issue pls any one can help me.modeam detail given below

modeam detail:
net provider : Reliance Net connect
name of manufacture : ZTE corporation, P.R.china
model no : MG 880

---

### Post by ramnarayan on 2008-12-09
Hi
this is a *Quick Guide to setting up a Reliance ZT 880 Reliance Data
card on Ubuntu Linux 8.10*

The guide should work for anything from Ubuntu 7.04 upwards and for
similar cards of reliance, bsnl and tata indicom.

This "how to" has been adapted from other "Guides and How To's" to setup
similar USB Data Cards, there are no guarantees and warranties – this
works for me and I have had no negatives so far. Also don't expect
support from Reliance for this. If you want another solution run a
search for "Ubuntu + zt 880 + India" you should get other usable results.

So Here goes

Open a terminal and run the following (copy and paste the command after
-$ or type them out carefully)

1. *mknod's* (it might already be there but making it again won't do any
harm)

-$ mknod /dev/ttyUSB0 c 188 0
-$ mknod /dev/ttyUSB1 c 188 1

2. *load usb serial driver*
~$ sudo modprobe usbserial vendor=0x19d2 product=0xfffd

(to know if the id and vendor is correct or same on your device) do
lsusb -v and see the appropriate entry) the above one is correct since I
did it on my machine

$ lsusb -v

major sections snipped and key parts *bolded* for your reference

Bus 001 Device 003: ID 19d2:fffd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.01
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        16
  *idVendor           0x19d2 *
  *idProduct          0xfffd *
  bcdDevice            0.00
  *iManufacturer           1 ZTE, Incorporated*
  iProduct                2 ZTE CDMA Tech
  iSerial                 3 Serial Number

3. *Run “dmesg”* to see if the device is attached to usb port
-$ dmesg

[  570.256642] usbcore: registered new interface driver usbserial
[  570.256670] usbserial: USB Serial support registered for generic
[  570.256689] usbserial_generic 1-1:1.0: generic converter detected
[  570.256878] usb 1-1: generic converter now attached to ttyUSB0
[  570.256888] usbserial_generic 1-1:1.1: generic converter detected
[  570.256962] usb 1-1: generic converter now attached to ttyUSB1
[  570.256972] usbserial_generic 1-1:1.2: generic converter detected
[  570.257050] usb 1-1: generic converter now attached to ttyUSB2
[  570.257076] usbcore: registered new interface driver usbserial_generic
[  570.257080] usbserial: USB Serial Driver core

to be clear remove device and run sudo dmesg -c – see output then attach
device and run sudo dmesg -c again

dmesg -c  clears the ring buffer and shows only latest changes.

*4. SETUP wvdial*

~$ sudo gedit /etc/wvdial.conf

copy and paste the below into your wvdial.conf file

[Modem0]
Modem = /dev/ttyUSB0
Baud = 115200
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
FlowControl = Hardware (CRTSCTS)

[Dialer zt880]
Username = yourphonenumber
Password = yourphonenumber
Phone = #777
Stupid Mode = 1
Inherits = Modem0

save and exit

*5. Unplug and replug the USB device*

you can run dmesg -c to know whats happening

*6. FINALLY*
run

~$ sudo wvdial zt880

which should result in:

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Dec  9 13:06:48 2008
--> Pid of pppd: 11812
--> Using interface ppp0
--> pppd: &#65533;_[07]
--> pppd: &#65533;_[07]
--> pppd: &#65533;_[07]
--> pppd: &#65533;_[07]
--> local  IP address 220.226.82.219
--> pppd: &#65533;_[07]
--> remote IP address 220.224.135.75
--> pppd: &#65533;_[07]
--> primary   DNS address 202.138.103.100
--> pppd: &#65533;_[07]
--> secondary DNS address 202.138.96.2
--> pppd: &#65533;_[07]

* 7. Exiting*
Control C in the terminal and the connection should close

Happy Surfing

*Other Minor tips*
1. to copy or paste from or into a terminal use shift+control+ c or v
2. terminal means a command line interface tool (can be accessed by
Applications &#8594; Accessories &#8594; terminal)
3. If you don't understand what a command does run -$ man “command” this
should show you the man pages of this command
4. You can rename the wvdial dialer name “zt880” to anything you like
and when running wvdial remember the name you chose and run -$ wvdial
“yourchosenname” to access the internet

***
hope this helps

regards
ram

---

