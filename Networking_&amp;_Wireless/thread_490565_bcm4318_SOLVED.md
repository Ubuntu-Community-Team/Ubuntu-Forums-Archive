---
title: "bcm4318 SOLVED"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by anilv on 2007-07-02
Hi

Just check the following. May resolve your broadcom bcm4318 problem. I followed the tutorial for installing the driver for bcm4318.

[http://tecpages.com/installing-and-configuring-bcm4318-broadcom-driver-using-ndiswrapper/](http://tecpages.com/installing-and-configuring-bcm4318-broadcom-driver-using-ndiswrapper/)

Thanks
Anil

---

### Post by exitmusic on 2007-07-03
hi i was able to install the driver, but after i check it's saying 'driver is invalid'. what shall i do next? thanks..

---

g@theotherlaptop:~$ ndiswrapper -mi /home/g/Desktop/bcmwl5.inf
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
g@theotherlaptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!

---

### Post by kevdog on 2007-07-03
Remove the driver,

sudo ndiswrapper -r bcmwl5

Then try the following:

sudo ndiswrapper -i /home/g/Desktop/bcmwl5.inf

I think the above is a little bit different than the syntax contained in your post.  You also need to make sure that bcmwl5.inf and the corresponding .sys file are located on the Desktop or in the /home/g/Desktop folder

---

### Post by kiddyfurby on 2007-07-03
With native driver, bcm4318 runs at 11Mbps
just install gcm43xx-fwcutter from the repos

---

