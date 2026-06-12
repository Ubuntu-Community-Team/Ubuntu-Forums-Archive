---
title: "wlan0 won't appear on ifconfig/iwconfig"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by bardia2 on 2014-05-10
I have an ARM device and I use wifi usb for wireless networking stuff. When I turn the device on and type ifconfig or iwconfig command I see no wlan0 interface, Although the wifi usb device will show on lsusb command.
This point is intresting that there is an application on the device itself for wireless networking and when I run and start to use that application and do for example a wifi networks search and then close that application, after that when I type ifconfig or iwconfig command I will see wlan0 interface and can deal with it.
My problem is how can I see wlan0 interface with just writing some commands on terminal and without running any specific application.
Thank You Guys!

---

### Post by twinkel1961 on 2014-05-10
either the lan driver is missing or your OS is not bringing up the network interface.
you can investigate which drivers are loaded by running lsmod.
if you run a
[FONT=Comic Sans MS]sudo tail -f /var/log/kernel.log[/FONT]
in a separate terminal, you can see what's happening when you start the other application.

---

