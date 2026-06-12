---
title: "WUSB54Gv1 install problem with ndiswrapper"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by ubergam3r on 2007-04-15
Hi downloaded ndiswrapper and copied all the driver filies from a disk, 
I type in the following command as told in the install doc and get the following error, i know nothing about linux as i thought id start using it today.

~$ ndiswrapper -i WUSB54G.inf
Installing wusb54g
Unable to create directory /etc/ndiswrapper/wusb54g. Make sure you are running as root

How do i fix this/ "run it as a root"?

---

### Post by Floppyjoe on 2007-04-15
> **ubergam3r said:**
> Hi downloaded ndiswrapper and copied all the driver filies from a disk, 
I type in the following command as told in the install doc and get the following error, i know nothing about linux as i thought id start using it today.

~$ ndiswrapper -i WUSB54G.inf
Installing wusb54g
Unable to create directory /etc/ndiswrapper/wusb54g. Make sure you are running as root

How do i fix this/ "run it as a root"?

execute with sudo prefix
```
sudo ndiswrapper -i WUSB54G.inf
```
to delete your invalid driver do this
```
sudo ndiswrapper -e drivername
```
to list drivers do this
```
ndiswrapper -l
```

---

