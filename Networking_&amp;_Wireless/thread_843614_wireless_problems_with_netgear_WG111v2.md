---
title: "wireless problems with netgear WG111v2"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by civillian on 2008-06-28
I recently set up a wireless network in my home, using a netgear router, and for other computers which I work at (two of which are ubuntu 8.04) the netgear WG111v2 usb wireless adapter.

I set up the drivers using a howto (basically, installing the drivers using ndiswrapper), the gist of which was as follows

> All the following has to be done as a super user.

First blacklist any existing drivers that might conflict.

-----------------------------------------------------------------------------------------------

> gedit /etc/modprobe.d/blacklist				(then add the following text to the bottom of the file: ...)



#Netgear conflicting drivers

blacklist islsm

blacklist islsm_pci

blacklist islsm_usb

blacklist prism2_usb

blacklist rtl8187

blacklist r8187b

-----------------------------------------------------------------------------------------------

> ndiswrapper -i <path to file>/netwg111.inf 		(install the drivers)

> ndiswrapper -l 							(check it's installed)

> depmod -a

> modprobe ndiswrapper						(not sure what this does, but it says to do it)

> ndiswrapper -m							(this may say "modprobe config already contains directive" but carry on)

> iwconfig wlan0							(should give some information)

> iwlist wlan0 scan							(show information about access point, hopefully)



> gedit /etc/modules							(then add the following text to the bottom of the file: ...)



ndiswrapper				

-----------------------------------------------------------------------------------------------

Now insert the USB adaptor

-----------------------------------------------------------------------------------------------

> ndiswrapper -l 							(should now say driver installed, hardware present)

-----------------------------------------------------------------------------------------------

If there is a network configuration option in the System menu,

use it to set up the following settings:

ESSID = *******
WPA (or WPA2) passphrase = ******************

This seemed to work, since after following the above howto (which is paraphrased) I plugged in the usb adapter and it registered my network and connected. However after a reboot the usb adapter registers the network and 'connects' however, when I try to check the network using
```
iwlist wlan0 scan
``` I am greeted by > wlan0     Interface doesn't support scanning.

I hope someone can answer my question, or tell me what to look for, since I'd dearly like to ditch my 20 metre network cable...

---

