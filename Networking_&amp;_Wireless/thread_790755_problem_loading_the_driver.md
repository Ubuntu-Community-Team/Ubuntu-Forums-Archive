---
title: "problem loading the driver"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by LPi on 2008-05-11
hello everybody 
i 've a problem in loading the network driver , 
i use senao eub 362 .
i installed it with ndiswrapper .
i used this command to the status of the driver installed or not 
ndiswrapper -l 
and it shows that the driver is already installed 
i tried to use this command to load it but nothing happens 
modprobe ndiswrapper

can anyone help?

---

### Post by james_vanb on 2008-05-11
If the driver has been loaded, I assume you ran:

sudo ndiswrapper -i

Once driver loaded, issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo gedit /etc/modules (or mousepad if using xubuntu)

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

---

