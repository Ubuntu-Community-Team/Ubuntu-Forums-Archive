---
title: "Linksys AE2500 dongle"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by mjalberts13 on 2013-12-06
Hey everyone,

I just started using Ubuntu yesterday and I am trying to install a windows driver for my wireless dongle(Linksys AE2500), but I don't understand how to install ndiswrapper. Synaptic Package Manager has the 1.57 version of ndiswrapper and I would like to install the 1.59 version from here: [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/). I downloaded the ndiswrapper-1.59.tar.gz file which is 200kb and I extracted it and then: sudo su, make clean, make, make install and it all executed succesfully but I am can not find "Windows Wireless Drivers" via Dash Home. I am running Ubuntu 12.04 LTS. I am currently on a wired connection to resolve the wireless issue before I move this computer to another room.

Thanks
Martin

Edit: When I type "ndiswrapper" in the terminal I get:
mj@mj-MS-7293VP:~$ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

Edit2: SOLVED!!!:D. I used these steps... THANK YOU to the guy who posted that.
[http://ubuntuforums.org/showthread.php?t=1805830&page=8&p=11811107#post11811107](http://ubuntuforums.org/showthread.php?t=1805830&page=8&p=11811107#post11811107)

---

