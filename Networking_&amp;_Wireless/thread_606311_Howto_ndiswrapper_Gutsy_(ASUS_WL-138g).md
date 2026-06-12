---
title: "Howto ndiswrapper Gutsy (ASUS WL-138g)"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by Stinger on 2007-11-07
**The hard way.**
(The easy way , scroll down)

This card will only work with ndiswrapper so you'll need to install the ndiswrapper packages first.
Go to System > Administration > Synaptic-packagemanager and look for these packages (a simple search for ndiswrapper should bring them up):

ndiswrapper-common 1.43-1ubuntu2 

ndiswrapper-utils-1.9 1.43-1ubuntu2 

Install both packages.

Now we need the windows driver from the ASUS installation CD-rom , it should be located in Driver > WinXP , [COLOR="Red"]don't use the driver from ASUS Website it screws up your system[/COLOR] 
This driver from Planet Technology WL-8313 works
[ftp://ftp1.planet.com.tw/Wireless_Lan/WL-8313/DR-WL8313v230.zip]("ftp://ftp1.planet.com.tw/Wireless_Lan/WL-8313/DR-WL8313v230.zip")
, copy the 2 files mrv8k51.inf and MRV8K51.sys to your /home/"yourname"/
Installation from terminal.
```

sudo ndiswrapper -i mrv8k51.inf
``` 

then ```
sudo ndiswrapper -m
```to make the module alias in   the /etc/modprobe.d/ndiswrapper file , here is mine.
> alias wlan0 ndiswrapper
And to load the module at boot time , add "ndiswrapper" to your /etc/modules file ,
```
sudo gedit /etc/modules
``` remember to save the file ,Here is my /etc/modules file.
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper


To check the driver do ```
ndiswrapper -l
``` it should give > Installed drivers:
mrv8k51         driver installed, hardware present , Now reboot and setup your card using System > Administration > Network.


**The easy way.**

Download the [ndisgtk package]("http://packages.ubuntu.com/gutsy/net/ndisgtk") ( and the windowsdriver if you need it , see the link at the top of this post ) prior to installation , save it on a usb-stick or a floppydisc.

doubleclick the "ndisgtk_0.7.2-1ubuntu1_i386.deb" package to get it installed , it will automatically pick up the ndiswrapper-common and the ndiswrapper-utils pakages.

Go to System>Administration>Windows Wireless Drivers and use "Install New Driver" to browse to the mrv8k51.inf file.

Now reboot and setup your card using System > Administration > Network.

Please check your /etc/modules file and see if "ndiswrapper" has been added to the end of the file , if not do:
```
sudo gedit /etc/modules
```and add "ndiswrapper" , remember to save the file ,Here is my /etc/modules file.
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

Good luck :)

---

