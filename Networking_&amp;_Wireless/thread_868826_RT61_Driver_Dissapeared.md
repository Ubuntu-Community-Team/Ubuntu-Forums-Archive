---
title: "RT61 Driver Dissapeared"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by rashwan on 2008-07-24
Hi,
First of all i would like to thank the "Knowledge" angles who have that great interest to share their knowledge.

am using Ubuntu 8.04 , and my wLan DWL-G510 RT61 Chipset which have been installed by default and working well when the system installed
but as a newbie finds attract in trying things i have got my driver removed

i was trying to install aircrack-ng module driver and i have successfully loaded the new driver but the old one removed completely
```
rashwan@rashwan:~$ lsmod | grep rt61
rt61                  209028  1 
rashwan@rashwan:~$
``` 
also that driver works on monitor mode only and i would like to run the network manager in GUI mode so how can i have my default driver back
and next time how can i SWITCH between drivers to use one of them and use the other next time HOPE THE PROBLEM ARE CLEARLY DEFINED

sorry for disturbing..and thanks for helping Newbie

---

### Post by Ayuthia on 2008-07-24
> **rashwan said:**
> Hi,
First of all i would like to thank the "Knowledge" angles who have that great interest to share their knowledge.

am using Ubuntu 8.04 , and my wLan DWL-G510 RT61 Chipset which have been installed by default and working well when the system installed
but as a newbie finds attract in trying things i have got my driver removed

i was trying to install aircrack-ng module driver and i have successfully loaded the new driver but the old one removed completely
```
rashwan@rashwan:~$ lsmod | grep rt61
rt61                  209028  1 
rashwan@rashwan:~$
``` 
also that driver works on monitor mode only and i would like to run the network manager in GUI mode so how can i have my default driver back
and next time how can i SWITCH between drivers to use one of them and use the other next time HOPE THE PROBLEM ARE CLEARLY DEFINED

sorry for disturbing..and thanks for helping Newbie

I am thinking that you should be able to use Network Manager with the rt61 module.  Have you tried changing the mode back to managed?  I think this is how you do it:
```
sudo ifconfig wlan0 down
sudo dhclient -r
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
```
However, if you want to use the other one again, I think that it was the rt61pci:
```
sudo modprobe -r rt61
sudo modprobe rt61pci
sudo ifconfig wlan0 up
```

---

### Post by rashwan on 2008-07-24
Hi again thanks for helping anyway...
i've tried what you said here is what i got
```
rashwan@rashwan:~$ sudo dhclient -r
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wlan0: unknown hardware address type 801
wlan0: unknown hardware address type 801
Listening on LPF/wlan0/
Sending on   LPF/wlan0/
Listening on LPF/eth0/00:04:4b:07:28:95
Sending on   LPF/eth0/00:04:4b:07:28:95
Sending on   Socket/fallback
rashwan@rashwan:~$ sudo iwconfig wlan0 mode managed
rashwan@rashwan:~$ sudo ifconfig wlan0 up
rashwan@rashwan:~$ sudo modprobe -r rt61
FATAL: Module rt61 is in use.
rashwan@rashwan:~$ sudo modprobe rt61pci
FATAL: Module rt61pci not found.

```
i can see networks in Network manager but "0" signal and cant connect

---

### Post by Ayuthia on 2008-07-24
> **rashwan said:**
> Hi again thanks for helping anyway...
i've tried what you said here is what i got
```
rashwan@rashwan:~$ sudo dhclient -r
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wlan0: unknown hardware address type 801
wlan0: unknown hardware address type 801
Listening on LPF/wlan0/
Sending on   LPF/wlan0/
Listening on LPF/eth0/00:04:4b:07:28:95
Sending on   LPF/eth0/00:04:4b:07:28:95
Sending on   Socket/fallback
rashwan@rashwan:~$ sudo iwconfig wlan0 mode managed
rashwan@rashwan:~$ sudo ifconfig wlan0 up
rashwan@rashwan:~$ sudo modprobe -r rt61
FATAL: Module rt61 is in use.
rashwan@rashwan:~$ sudo modprobe rt61pci
FATAL: Module rt61pci not found.

```
i can see networks in Network manager but "0" signal and cant connect

Can you post the results of:
```
lsmod|grep rt61
```

Also, how did you remove your other driver?  Do you recall the name of it?

---

### Post by rashwan on 2008-07-24
```
 lsmod | grep rt61
rt61                  209028  1
```

thats it

---

### Post by Ayuthia on 2008-07-24
Sorry about that.  I just saw that you already posted the information in your first post.

Normally, sudo modprobe -r rt61 would just remove the module without complaining when it is not attached to any other module.  You might try doing ifconfig wlan0 down then the modprobe -r.  Otherwise, I am not for sure about why it cannot be removed.

---

### Post by rashwan on 2008-07-25
its not the problem to remove the rt61 module its about reinstalling the rt61pci moudle which have been installed by default when ubuntu 8.04 installed
thats it where can i get it

---

