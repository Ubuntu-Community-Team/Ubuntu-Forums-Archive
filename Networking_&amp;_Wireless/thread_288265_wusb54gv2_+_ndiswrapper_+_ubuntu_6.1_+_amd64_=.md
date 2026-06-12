---
title: "wusb54gv2 + ndiswrapper + ubuntu 6.1 + amd64 = ?"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by raging hormones on 2006-10-29
Hey all, longtime lurker first time poster

I just made the switch from SUSE to ubuntu 6.1 running on an AMD 64 dual core processor.  Like many others here, I have a problem with ndiswrapper, and the weird thing is I had it working perfectly on the same machine running the 64 bit version of SUSE 10.1.  The driver, and hardware are recognized:

root@flower:/home/allen/Desktop/WUSB54Gv4_20050503/Drivers/WUSB54Gv2# ndiswrapper -l
installed drivers:
wusb54gv2               driver installed, hardware (13B1:000A) present 

Now when I try and set things up, I get:

root@flower:/home/allen/Desktop/WUSB54Gv4_20050503/Drivers/WUSB54Gv2# ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 714.

running $modprobe ndiswrapper apparently does nothing because iwconfig shows the same thing before and after I run modprobe:

root@flower:/home/allen/Desktop/WUSB54Gv4_20050503/Drivers/WUSB54Gv2# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

What throws me is that in the setup ndiswrapper adds wlan0 while iwconfig doesn't show that as a possibility, I don't know if that is significant but from what I remember when I had it working before wlan0 was shown even when there was no wireless extension.

As a final note I would greatly appreciate any input or suggestions as:

1. I have spent the better part of the weekend on this and would not be asking if I had not racked my brain and scoured google.

2.  I really don't want to go back to suse, that distro had gave me headaches, mostly because of the package manager.

3.  My roomates won't let me keep the cable modem in my room forever!!!

---

### Post by raging hormones on 2006-11-18
I have the same exact problem and cannot figure it out to save my life.

---

