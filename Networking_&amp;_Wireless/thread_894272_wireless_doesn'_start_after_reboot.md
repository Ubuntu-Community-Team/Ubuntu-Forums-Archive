---
title: "wireless doesn' start after reboot"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by drumanart on 2008-08-19
Hi folks this is an easy one (hopefully).
My wireless connection want start after restating the system (HARDY).

My "interfaces" file shows this:
**sudo gedit /etc/network/interfaces**

auto lo
iface lo inet loopback
iface wlan0 inet dhcp
wireless-key 6A2D8236C0  //key invented
wireless-essid SpeedTouch085F4D

auto wlan0


My "rc.local" file shows this:

**sudo gedit /etc/rc.local**

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


#iwconfig wlan0 essid SpeedTouch085F4D mode Managed channel 03
#iwconfig wlan0 key 6A2D8236C0  //key invented

exit 0


To start my wireless connection I have to reconfigure the network-manager everytime the coputer was rebooted.

thks Martin

---

