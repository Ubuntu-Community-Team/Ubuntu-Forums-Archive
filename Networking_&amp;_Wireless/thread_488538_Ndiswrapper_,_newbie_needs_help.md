---
title: "Ndiswrapper , newbie needs help"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by qzonk on 2007-06-30
Im using feisty fawn and got this far with the ndiswrapper part of installing the
windows drivers for my Senao Sub 362 USB wifi device, it uses the Atheros AR5523 chipset

henry@qzonk:~/wireless$ lsusb
Bus 003 Device 003: ID 0cf3:0002 Atheros Communications, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000

henry@qzonk:~/wireless$ ndiswrapper -v
utils Error: no version specified!
driver version: 1.38
vermagic: 2.6.20-16-generic SMP mod_unload 586

henry@qzonk:~/wireless$ ndiswrapper -l
athfmwdl : driver installed
device (0CF3:0002) present
net5523 : driver installed
device (0CF3:0002) present

---

### Post by kevdog on 2007-06-30
Try installing the utils module for the ndiswrapper -- notice the error in the ndiswrapper -v statement.

I think you can type:
sudo aptitude install ndiswrapper-utils-1.9
to do this.

After doing the above you verify with:
ndiswrapper -v 
to ensure the utils package 1.9 is mentioned

Mine for example says this:
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 


As far as the driver installation your help, unless Im mistaken I think you should have only one driver listed when you do ndiswrapper -l
Try removing one of them: sudo ndiswrapper -r ***** <--driver name here

I dont know which one you should remove since likely you only need one of them with your card.  You alone know the detalis of your card and what driver you should be using.

---

