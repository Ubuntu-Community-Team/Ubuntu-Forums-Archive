---
title: "ARRRGGGHHH....MA111 wireless driver making me nuts!!!"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by Caermundh on 2007-06-09
OK, im trying to install and configure the Netgear MA111 wireless driver under Ubuntu 7.04 alternate install. I've performed the following steps:

1) sudo apt-get install ndiswrapper-common
(this installed with no errors)

2) sudo apt-get install ndiswrapper-utils-1.9
(this also installed with no errors)

3) sudo gedit /etc/hotplug/blacklist
(added "prism2_usb" to end of file - i believe this prevents the native drivers from loading and possibly conflicting with the drivers loaded by ndiswrapper?)

4) cd ma111_2.5beta/drivers/winxp/

5) sudo ndiswrapper -i ma111.inf
(this installs the .inf file as the driver for ubuntu to use with the Netgear MA111 right?)

6) sudo ndiswrapper -l
(response was:
 "netma111:driver installed"
"device (0846:4110) present (alternate driver: prism2_usb)"
I believe this is telling me the device is present AND drivers installed right?)

7) sudo gedit /etc/modules
(added "ndiswrapper" so that ndiswrapper will be automatically loaded at boot)

8) sudo gedit /etc/network/interfaces
( added the following lines:

iface wlan0 inet dhcp
wireless_mode managed
wireless-essid <my essid>
wireless-enc on
wlan-ng-key0 nn:nn:nn:nn:nn
wlan-ng-authtype opensystem
wireless-key nnnnnnnnnn

all of this is what i have to add to connect to an encrypted router right?)

after all that, i restarted the machine, but wireless still doesnt work! This process appearently works for everyone else though. I dont get it. Have i missed a step somewhere?

Something else, when i go to System->Administration->Network, i see "Wired connection(wlan0), Address:DHCP" instead of "Wireless connection, ESSID:<my essid> ADDRESS: DHCP" liked everyone else says you should see. Is this the problem? if so why am i seeing "wired connection(wlan0) instead of the "wireless connection" like im suppsed to?

---

### Post by evilgreenie on 2007-06-15
Hey Caermundh - did you ever get a solution to this problem? I've got exactly the same issue...

I sucessfully installed MA111 driver under ndiswrapper on one machine, but on a second laptop,the wlan0 interface is convinced it's a wired connection, not a wireless ..

---

