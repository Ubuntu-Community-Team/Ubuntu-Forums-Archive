---
title: "Belkin Wireless G USB Adapter w/ Edgy"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by RyanPower on 2007-02-14
I've searched high and low on the web and every other "solution" hasn't worked for me. I'm trying to get my Belkin Wireless G USB Adapter to work with my fresh install of Edgy. I've put the Windows drivers for it through ndiswrapper akd it says they are okay. But wlan0 still isn't up.

Here's the output for "sudo ifup wlan0:"

```
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

And here is /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
auto wlan0
```

Thanks.

---

### Post by fallasteeni on 2007-02-18
Same exact card, same exact problem. Can anyone PLEASE help?

---

### Post by speedwolf on 2007-02-18
Ok, right I'm here to answer all your prayers.
Thanks to entirely to **Giri**, over at the #ndiswrapper IRC room, who held my hand through the entire process (and no matter how angry he got with me) he managed to fix all the problems.

This applies only to the F5D7051 with the Broadcom BCM4320 chipset. To help any of you have lost your installation CD, I've attached the three files you need to get this party started.

**Step 1:**
Use the Synaptics Package manager to uninstall the default version of ndiswrapper and all the utils and so forth that you may have already on your system.

Then you need to get and compile the latest version from sourceforge. You can find all the information you need here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Downloading](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Downloading)

**Step 2:**
Download the drivers from the bottom of this post and untar them to somewhere obvious. The reason for this will become clear soon. I'm going to assume that you put them on the Desktop (remember the cap D) and for the purposes of the tutorial that's what I'll use.

**Step 3:**
Fire up a terminal.
Type:
```
sudo ndiswrapper -i Desktop/BCMRNDIS.INF
```
You'll get it trying to install two other files, it won't work. If you type: 
```
ndiswrapper -l
```
You'll see that it returns
```
bcmrndis : driver invalid!
```
This is because it hasn't copied the two .sys files over into the folder with it during installation. Also note the change from upper to lower case.

**Step 4:**
In your terminal type:
```
sudo cp Desktop/RNDISMPKF.SYS /etc/ndiswrapper/bcmrndis/rndismpkf.sys
sudo cp Desktop/USB8023K.SYS /etc/ndiswrapper/usb8023k.sys
```
Pay careful attention to the case again. Enter:
```
ndiswrapper -l
```
This time you get:
```
bcmrndis : driver installed
device (050d:7051) present
```

**Step 5**
Almost there, only a couple of steps to go.
In your terminal type:
```
sudo gedit /etc/udev/rules.d/z25_local_rules
```
Then copy and paste this into the new text file that's been created:
```
BUS=="usb", SYSFS{idProduct}=="7051", SYSFS{idVendor}=="050d", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

```
Save and close it.

**Step 6**
Again, in your terminal. type:
```
sudo modprobe ndiswrapper
```
This loads the service up (I think!). If you type:
```
dmesg | tail -5
```
You can see that it's suddenly seeing your wlan0. Make your settings changes, SSID stuff, WEP   in *System>Administration>Networking* and so on and you should be ready to roll.

As I said at the beginning I can't claim responsibility for this how-to, it's all down to Giri at #ndiswrapper.

I spent hours and hours and hours trying to do this and I really hope it prevents someone else having to go through the hair pulling that I did.

---

### Post by elephanttoast on 2007-09-01
Got the same problem with the BELKIN wireles G USB card.
- ndiswrapper module is loaded
- ndiswrapper -l shows the bcmrndis driver is installed and the device is present
- done the suggested entries in /etc/udev/rules.d/z25_local_rules
- wlan0 is configured in /etc/network/interfaces
- lsusb shows the Belkin device
- compiled the newest version of ndiswrapper from sourceforge.net (1.47)
- compared the windriver with the versions that speedwolf posted (no difference)

BUT : 
- iwconfig shows no wlan0
- ifup wlan0 up shows :
              SIOCSIFADDR : No such device
              wlan0: ERROR while getting interface flags: No such device
              wlan0: ERROR while getting interface flags: No such device
              Bind socket to interface: no such device
              Failed to bring up wlan0.
              ignoring unknown interface up=up

Has anyone suggestions - HEEEELP ??

---

### Post by peebly on 2007-09-01
noticed the Broadcom chipset.

Did you try it using the method in this thread.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by elephanttoast on 2007-09-01
Thanks for the hint, looks like really nice and easy project.
But it seems to be made for pci-cards - my usb-stick was not found. 
I read somewhere else in this forum that the Belkin 7051 has a BCM4320 chipset. 
Anyway i think i`ll try to get a pci card with a BROADCOM chipset or an other (nativ) supported chipset.

---

### Post by aitutaki on 2008-01-15
cheers so much!

---

### Post by griffij8 on 2008-02-27
Just want to say I loaded 7.10 Gutsy just last week and the install was as easy as anything but for my network connection. Hours of trawling through many posts and websites and finally I found this help and it all works. Belkin F57051 working brilliantly! Big thank you to speedwolf and Giri but the crucial step for me was Step 4 and Step 6.

---

