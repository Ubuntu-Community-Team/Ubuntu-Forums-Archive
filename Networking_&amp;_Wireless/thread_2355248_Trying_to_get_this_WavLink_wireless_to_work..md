---
title: "Trying to get this WavLink wireless to work."
date: 2017-03-10
forum: Networking &amp; Wireless
---

### Post by joepro83 on 2017-03-10
I was able to download the driver stuff from online. It's a WavLink AC1200, dual band. But installing the thing is proving difficult since the only automated installations are executables for Windows. It appears to have Linux drivers as well, but there doesn't seem to be an automatic way to install it. And being new to Linux, I have no clue how to get it to where it all needs to be, or if maybe there's a set of terminal commands to get it installed. Anyone have experience with these? I can take screen caps of the folders/drivers associated with the device if needed.

---

### Post by deadflowr on 2017-03-10
*Thread moved to **Networking & Wireless**.*

---

### Post by oldrocker99 on 2017-03-10
Here's a solution: Ndiswrapper is a program that allows Windows wireless drivers to work with Linux. The command below will install the GUI, which makes it easy. Just point it at the .inf file in the driver folder.```
sudo apt install ndisgtk
```

Look for "Windows Wireless Drivers" to run it, in Administration.

---

### Post by joepro83 on 2017-03-11
There was an error installing that program. Reported the error and was  then redirected to a page where others are experiencing the error as  well. Didn't look like there's currently any solution to that  error/program install.

---

### Post by chili555 on 2017-03-11
I assume this is a USB device. Please insert the device and run and then post:```
lsusb
```

---

### Post by joepro83 on 2017-03-11
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 04d9:1605 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have two wireless adapters in. I believe the first one listed is the one I'm trying to get to work. The second is the one that works, but not the one I care about having.
Thanks!

---

### Post by wildmanne39 on 2017-03-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chili555 on 2017-03-12
> ID [COLOR="#FF0000"]0bda:8812 [/COLOR]Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN AdapterThis device is supported by the driver rtl8812au. 

[http://packages.ubuntu.com/search?keywords=rtl8812au-dkms](http://packages.ubuntu.com/search?keywords=rtl8812au-dkms)

Which Ubuntu version do you have?```
uname -r
lsb_release -a
```

---

### Post by joepro83 on 2017-03-12
```
4.8.0-41-generic
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
```

---

### Post by chili555 on 2017-03-13
Please try, with a temporary internet connection:```
sudo apt-get update
sudo apt-get install rtl8812au-dkms
```Reboot and your wireless should be working.

---

### Post by joepro83 on 2017-03-13
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-dejavu fonts-dejavu-extra fonts-gargi fonts-wqy-microhei ioquake3
  ioquake3-server libappindicator1 libindicator7 libopusfile0
  libsfml-audio2.3v5 libsfml-graphics2.3v5 libsfml-system2.3v5
  libsfml-window2.3v5 linux-headers-4.8.0-36 linux-headers-4.8.0-36-generic
  linux-image-4.8.0-36-generic linux-image-extra-4.8.0-36-generic
  marsshooter-data openarena-081-maps openarena-081-misc openarena-081-players
  openarena-081-players-mature openarena-081-textures openarena-085-data
  openarena-088-data openarena-data openarena-oacmp1 python3-xlib
  redeclipse-common redeclipse-data uswsusp
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  rtl8812au-dkms
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,024 kB of archives.
After this operation, 7,778 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 rtl8812au-dkms all 4.3.8.12175.20140902+dfsg-0ubuntu2 [1,024 kB]
Fetched 1,024 kB in 3s (261 kB/s)         
Selecting previously unselected package rtl8812au-dkms.
(Reading database ... 248727 files and directories currently installed.)
Preparing to unpack .../rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb ...
Unpacking rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu2) ...
Setting up rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu2) ...
Loading new rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
First Installation: checking all kernels...
Building only for 4.8.0-41-generic
Building initial module for 4.8.0-41-generic
Error! Bad return status for module build on kernel: 4.8.0-41-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log for more information.
```

Which redirected me to here: [https://bugs.launchpad.net/ubuntu/+source/rtl8812au/+bug/1637059](https://bugs.launchpad.net/ubuntu/+source/rtl8812au/+bug/1637059)

---

### Post by chili555 on 2017-03-13
I'm trying to work out another solution. In the meantime, I recommend that you register and add to the 'does this affect you' button.

I hope to have a better fix soon.

EDIT: You might try the process at post #15 and following: [https://ubuntuforums.org/showthread.php?t=2353194](https://ubuntuforums.org/showthread.php?t=2353194)

---

### Post by joepro83 on 2017-03-13
That did it! Thanks for the find.

---

