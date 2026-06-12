---
title: "firmware-b43-installer won't install 14.04"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by chrrsgrvy on 2014-05-19
Hi
Last week I started replacing XP on a set of old Dell Inspiron 6400 laptops in our school with Ubuntu 14.04. Via the forums I learned to get the Broadcom BCM4311 (14e4:4311(rev 01)) by

1. Using sudo apt-get remove --purge bcmwl-kernel-source    immediately on restart after installation, and

2 Using sudo apt-get install firmware-b43-installer  on restarting again.

This worked fine for the first 8 laptops. On Friday it stopped working for me. Here is a terminal copy n' paste.


```
sen@sen14pc:~$ sudo apt-get install firmware-b43-installer 
[sudo] password for sen:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following package was automatically installed and is no longer required: 
  dkms 
Use 'apt-get autoremove' to remove it. 
The following extra packages will be installed: 
  b43-fwcutter 
The following NEW packages will be installed: 
  b43-fwcutter firmware-b43-installer 
0 upgraded, 2 newly installed, 0 to remove and 123 not upgraded. 
Need to get 29.3 kB of archives. 
After this operation, 146 kB of additional disk space will be used. 
Do you want to continue? [Y/n] y 
Get:1 [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty/main b43-fwcutter i386 1:018-2 [25.4 kB] 
Get:2 [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty/multiverse firmware-b43-installer all 1:018-2 [3,960 B] 
Fetched 29.3 kB in 1s (29.1 kB/s)             
Preconfiguring packages ... 
Selecting previously unselected package b43-fwcutter. 
(Reading database ... 164992 files and directories currently installed.) 
Preparing to unpack .../b43-fwcutter_1%3a018-2_i386.deb ... 
Unpacking b43-fwcutter (1:018-2) ... 
Selecting previously unselected package firmware-b43-installer. 
Preparing to unpack .../firmware-b43-installer_1%3a018-2_all.deb ... 
Unpacking firmware-b43-installer (1:018-2) ... 
Processing triggers for man-db (2.6.7.1-1) ... 
Setting up b43-fwcutter (1:018-2) ... 
Setting up firmware-b43-installer (1:018-2) ... 
No chroot environment found. Starting normal installation 
--2014-05-19 12:32:43--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2) 
Resolving [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com](www.lwfinger.com))... 173.254.28.119 
Connecting to [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com)|173.254.28.119|:80](www.lwfinger.com)|173.254.28.119|:80)... connected. 
HTTP request sent, awaiting response... 503 Service Unavailable 
2014-05-19 12:32:45 ERROR 503: Service Unavailable. 
 
dpkg: error processing package firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 8 
Errors were encountered while processing: 
 firmware-b43-installer 
E: Sub-process /usr/bin/dpkg returned an error code (1) 

```
Any idea as to why this process has ceased to work? Any help with the card working appreciated.



Chris

---

### Post by Hadaka on 2014-05-19
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```

---

### Post by chrrsgrvy on 2014-05-19
Thanks Hadaka. I should have mentioned I already tried that  ...

sen@sen14pc:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up firmware-b43-installer (1:018-2) ...
No chroot environment found. Starting normal installation
--2014-05-19 16:03:30--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
Resolving [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com](www.lwfinger.com))... 173.254.28.119
Connecting to [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com)|173.254.28.119|:80](www.lwfinger.com)|173.254.28.119|:80)... connected.
HTTP request sent, awaiting response... 503 Service Unavailable
2014-05-19 16:03:31 ERROR 503: Service Unavailable.

dpkg: error processing package firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 8
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
sen@sen14pc:~$

---

### Post by Hadaka on 2014-05-19
hi, let's first verify your pci id
```
lspci -n | grep 0280
sudo apt-get autoremove
sudo apt-get remove --purge bcmwl-kernel-source  #for good measure

```
then do,,
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
```
dont use the additional drivers 
```
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a

```
BOOT
then do,.
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
that help?

---

### Post by chrrsgrvy on 2014-05-19
Thanks again Hadaka

 I had to shut down the laptop and move it to another space to work on. When I switched it on the wifi indicator lit-up and I managed to successfully connect to the wireless network. I've rebooted several times since to check it's a stable connection, and it is. 

The last thing I did before moving to the new space was run *[COLOR=#000080]sudo apt-get install linux-firmware-nonfree[/COLOR]* in the terminal and copy and paste in post above.

I'm not sure why it's working now, given that I got this at end of install ....

[I][COLOR=#000080]dpkg: error processing package firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 8
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/I]

I'm a complete newbie to the forum, so sorry for pasting the code without the box around it   ..... i haven't figured that out yet.

Many thanks for your help. I hope when I continue with the rest of the laptops tomorrow it'll go smoothly.

---

### Post by Hadaka on 2014-05-19
Glad you got it working.

to use code tags you can click the "#" sign ...second row last colum on the reply page.
then copy and paste your code between the tags [ code]paste here[/ code]
or
you can type [ code]bunch of interesting stuff[/ code]  <---the word CODE needs to be in uppercase both ends and no spaces

---

