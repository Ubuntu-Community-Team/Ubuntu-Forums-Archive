---
title: "Linksys WUSB54GC"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by BartlebyScrivener on 2006-11-12
I have a Netgear wireless Access Point and a Pentium II running Edubuntu for my kid. 

Trying to connect using USB wireless. My network is dhcp. No static.

Tried to install the Ralink drivers using these instructions:

[http://home.kpnplanet.nl/~j.riechelman@kpnplanet.nl/](http://home.kpnplanet.nl/~j.riechelman@kpnplanet.nl/)

No flashing light on the usb stick. It works fine on Windows. Nothing on ubuntu, though when I test with:

modprobe -l rt73

it shows the directory where I installed the rt73 driver.

More info:

lsusb

Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 002: ID 13b1:0020 Linksys 
Bus 001 Device 001: ID 0000:0000  

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"rpd2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid rpd2

iface wmaster0 inet dhcp
wireless-essid rpd2

Any help much appreciated. I've been googling and combing these pages with no luck.

rd

---

### Post by BartlebyScrivener on 2006-11-19
Anybody having trouble installing this USB stick, should follow the instructions for the the Belkin F5D7050 ver 3000 Ralink rt73 at:

[http://tinyurl.com/ygparp]("http://tinyurl.com/ygparp")

The WUSB54GC uses the same Ralink drivers. Just need to enter the proper device ID, but the Linksys ID particulars are included in the example on the instructions page.

Good luck,

rd

---

