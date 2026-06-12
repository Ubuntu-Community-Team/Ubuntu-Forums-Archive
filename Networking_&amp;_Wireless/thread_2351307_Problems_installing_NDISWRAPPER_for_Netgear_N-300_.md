---
title: "Problems installing NDISWRAPPER for Netgear N-300 USB adapter"
date: 2017-02-01
forum: Networking &amp; Wireless
---

### Post by cheese.biscuit on 2017-02-01
I've finally got Ubuntu up and running on my Shuttle XPC SG31G desktop, and an old Dell. Neither is giving me an option to connect to the wifi. The old dell laptop has a wifi card, so I think I can get that working with instructions available online. But every solution I've tried for the Netgear adapter has failed. I'm hoping someone here can help point me in the right direction.

I am using 16.04.1 lts Ubuntu. My system is 64, rather than 32.

The device does show up. (It's the first one. 

```
 ~$ lsusb
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

```
I've tried installing NDISwrapper, but it seems like each solution is pointing to some drivers or other files not being successfully downloaded.

Here is what showed up in the terminal when I tried to install it a few minutes ago.

```
USER@USER:~$ tar zxvf ndiswrapper-version.tar.gz
tar (child): ndiswrapper-version.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
USER@USER:~$ sudo apt-get update
[sudo] password for USER: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Hit:2 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial InRelease         
Hit:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:4 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease        
Get:5 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:6 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Fetched 306 kB in 2s (134 kB/s)    
Reading package lists... Done
USER:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ndiswrapper' instead of 'ndiswrapper-common'
ndiswrapper is already the newest version (1.59-6).
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont fonts-unfonts-core fonts-wqy-microhei
  gnome-exe-thumbnailer icoutils libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0
  libgstreamer0.10-0:i386 libice6:i386 libsm6:i386 libxt6:i386
  ocl-icd-libopencl1:i386 odbcinst odbcinst1debian2 p11-kit-modules:i386
  ttf-mscorefonts-installer ttf-wqy-microhei unixodbc
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 279 not upgraded.
USER@USER:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version (1.59-6).
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont fonts-unfonts-core fonts-wqy-microhei
  gnome-exe-thumbnailer icoutils libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0
  libgstreamer0.10-0:i386 libice6:i386 libsm6:i386 libxt6:i386
  ocl-icd-libopencl1:i386 odbcinst odbcinst1debian2 p11-kit-modules:i386
  ttf-mscorefonts-installer ttf-wqy-microhei unixodbc
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 279 not upgraded.
arh: command not found
USER@USER:~$ arch
x86_64
USER:~$ cd ~/Desktopb/Broadcom_bcm43xx_USB_32_64bit_v2
bash: cd: /home/USER/Desktopb/Broadcom_bcm43xx_USB_32_64bit_v2: No such file or directory
USER@USER:~$ sudo ndiswrapper -i bcmn43xx64.inf
couldn't open bcmn43xx64.inf: No such file or directory at /usr/sbin/ndiswrapper line 162.
```



Thank you for your help!

---

### Post by wildmanne39 on 2017-02-02
*Thread moved to **Networking & Wireless for better support**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chili555 on 2017-02-02
Have you read this? [https://ubuntuforums.org/showthread.php?t=2264020](https://ubuntuforums.org/showthread.php?t=2264020)

> As of now, unless someone has another driver or process to try, I don't believe this device can be made to work correctly in Ubuntu 14.04 and later. Please don't ask me to help. I've tried everything I know of and it doesn't work.

---

### Post by cheese.biscuit on 2017-02-02
Thanks,I will do that in the future.

---

### Post by cheese.biscuit on 2017-02-02
I hadn't seen that. Oh well. I'll look around for one that is known to work with Ubuntu. Maybe I can sell this one or something.

Thank you!

---

