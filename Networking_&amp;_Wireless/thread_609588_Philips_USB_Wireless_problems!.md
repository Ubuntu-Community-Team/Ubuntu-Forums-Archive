---
title: "Philips USB Wireless problems!"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by Ohrid on 2007-11-11
Hello,
I can not have Philips CPWUA054 USB wireless adapter working properly on UBUNTU 7.o4 (2.6.20-16-generic)
These are the steps that I did:
Install ndiswrapper
Code: 
$ ndiswrapper -v

utils version: '1.9', utils version needed by module: '1.9'

module details:

filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko

version:        1.48

vermagic:       2.6.20-16-generic SMP mod_unload 586 
cd to directory with  CPWUA2D.*
Code:
$ sudo ndiswrapper -i CPWUA2D.inf

Password:

installing cpwua2d ...

forcing parameter EnableRadio from 0 to 1

$ 

Check the driver
Code:
$ ndiswrapper -l

cpwua2d : driver installed

$


As you can see the hardware is not detected.
Any suggestion?

---

