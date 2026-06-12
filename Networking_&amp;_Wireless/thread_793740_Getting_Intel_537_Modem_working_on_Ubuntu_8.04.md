---
title: "Getting Intel 537 Modem working on Ubuntu 8.04"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by arjayes on 2008-05-14
Please tell where I can get the modem drivers for an Intel 537 WinModem for Ubuntu Hardy . I have tried compiling the soure package mentioned here : [https://help.ubuntu.com/community/DialupModemHowto/Intel537EP](https://help.ubuntu.com/community/DialupModemHowto/Intel537EP) ([http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz](http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz)) I unpacked it and I followed the instructions given for Ubuntu 7.10
> 
sudo apt-get install build-essential
export MODEM_TYPE=537EP
sudo make clean
sudo make 537
sudo make install

but i get this when i try > sudo make 537
> 
   Module precompile check
   Current running kernel is: 2.6.24-16-generic
   /lib/modules...   autoconf.h exists
   autoconf.h matches running kernel
   version.h matches running kernel
2.6.24-16-generic
make[1]: Entering directory `/home/user1/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/user1/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: Leaving directory `/home/user1/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
2.6.24-16-generic
Failed to build driver

What am i doing wrong ?

---

### Post by chuckman78 on 2008-08-06
This might be too late but check this link:

[http://groups.google.com/group/ubuntu-modems/]("http://groups.google.com/group/ubuntu-modems/")

Regards,

Carlos
aka chuckman78.

---

