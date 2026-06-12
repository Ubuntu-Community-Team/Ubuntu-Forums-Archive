---
title: "Huawei ETS T1 2288 CDMA (WLL) phone not working on Hardy Heron"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by ramnarayan on 2008-08-10
Hi

We have a CDMA Wireless in Local Loop (WLL) Huawei ETS T1 2288 phone through which we access the internet (through BSNL service provider in India)

This works on fiesty (and i think gutsy) but it does not work on Hardy.

This is the process i have followed on fiesty (7.04)

uname -a
~$ uname -a 
Linux ram2-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux 

Result of dmesg -c 
~$ sudo dmesg -c 
[  391.793755] usb 1-1: new full speed USB device using uhci_hcd and address 6 
[  391.838450] usb 1-1: configuration #1 chosen from 1 choice 
[  391.842334] ti_usb_3410_5052: probe of 1-1:1.0 failed with error -5

Added the file
laptop:~$ sudo gedit /etc/udev/rules.d/026_ti_usb_3410.rules 

with the following lines

#TI USB 3410 
SUBSYSTEM=="usb_device" ACTION=="add" SYSFS{idVendor}=="0451",SYSFS{idProduct}=="3410" \ 
SYSFS{bNumConfigurations}=="2" \ 
SYSFS{bConfigurationValue}=="1" \ 
RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'"

***

After that ran dmesg -c again and this is the result

laptop:~$ sudo dmesg -c 
[   92.920387] usb 1-1: new full speed USB device using uhci_hcd and address 5 
[   92.965144] usb 1-1: configuration #1 chosen from 1 choice 
[   92.969036] ti_usb_3410_5052: probe of 1-1:1.0 failed with error -5 

At this stage on Fiesty we would get a message saying the device to be identified as a /dev/ttyUSB0 and it works

after which a appropriate entry is made in the wvdial.conf file

which is 
[Dialer 92]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = xxxxxxxxxx
Password = xxxxxxxxxx
PPPD Options = crtcts multilink usepeerdns lock defaultroute
AutoDNS = off
# Inherits = Modem0

 ***

So whats wrong – why is Hardy Heron not being able to pick up the device and configure it.

***
The same configuration works under Ubuntu 7.04 


would appreciate the help - since if it begins to work then i will upgrade to 8.04 

thanks
ram

---

### Post by smartboy08 on 2008-11-29
How it can be installed on Ubuntu 8.10?

---

### Post by jasir on 2009-05-10
i've upgraded to ubuntu 9.04
and got the same BSNL phone. any idea how to connect?

---

