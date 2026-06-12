---
title: "Broadcom Wireless 4318 driver is not getting installed in Ubuntu 13.10."
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by Varun_C on 2014-05-10
Command Tried:** lspci -nn | grep 0280**

2:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

Please help to resolve this issue.

I am new to Ubuntu

---

### Post by Hadaka on 2014-05-10
hi,please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by Varun_C on 2014-05-10
Thank You  for the help. Still Not able to use my WiFI.
Result for the commands are given below.

Code:
[TABLE="width: 500"]
[TR]
[TD]sudo apt-get remove --purge bcmwl-kernel-source[/TD]
[/TR]
[/TABLE]
***_Result:_***
   Building dependency tree        
 Reading state information... Done  
 The following packages were automatically installed and are no longer required:  
   dkms fakeroot linux-image-generic  
 Use 'apt-get autoremove' to remove them.  
 The following packages will be REMOVED: 
   bcmwl-kernel-source*  
 0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.  
 After this operation, 5,798 kB disk space will be freed.  
 Do you want to continue [Y/n]? y  
 (Reading database ... 193047 files and directories currently installed.)  
 Removing bcmwl-kernel-source ...  
 Removing all DKMS Modules  
 Done.  
 update-initramfs: deferring update (trigger activated)  
 Purging configuration files for bcmwl-kernel-source ...  
 update-initramfs: deferring update (trigger activated)  
 dpkg: warning: while removing bcmwl-kernel-source, directory '/usr/src/bcmwl-6.30.223.141+bdcom/lib' not empty so not removed  
 Processing triggers for initramfs-tools ...  
 update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic


Code:


[TABLE="width: 500"]
[TR]
[TD]sudo rm /etc/modprobe.d/blacklist-bcm43.conf[/TD]
[/TR]
[/TABLE]
***_Result:_***
rm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory

files inside ***/etc/modprobe***.***d/ ***are:

   
blacklist-ath_pci.conf       blacklist-modem.conf  
 blacklist.conf               blacklist-oss.conf  
 blacklist-firewire.conf      blacklist-rare-network.conf  
 blacklist-framebuffer.conf   blacklist-watchdog.conf


Code:

[TABLE="width: 500"]
[TR]
[TD]sudo apt-get install linux-firmware-nonfree[/TD]
[/TR]
[/TABLE]
_***Result:***_

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  dkms fakeroot linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Code:

[TABLE="width: 500"]
[TR]
[TD]sudo modprobe b43[/TD]
[/TR]
[/TABLE]
[U][I][B]
Result:[/B][/I][/U]
libkmod: ERROR ../libkmod/libkmod.c:554 kmod_search_moddep: could not open moddep file '/lib/modules/3.13.0-24-generic/modules.dep.bin'



Please see these results and help.


Thank You Vary Much...

---

### Post by Hadaka on 2014-05-10
Hi, please do..
```
sudo rm /usr/src/bcmwl-6.30.223.141+bdcom/lib
```

*If this is a new install, i would suggest re-installing the os, you have
some very corrupt files.
thanks

---

### Post by Varun_C on 2014-05-10
Re-installed the OS.

Tried the commands again.

Last command result is given

Code:

[TABLE="class: cms_table, width: 500"]
[TR]
[TD]sudo modprobe b43[/TD]
 [/TR]
 [/TABLE]

 [U][I][B]
Result:[/B][/I][/U]
libkmod: ERROR ../libkmod/libkmod.c:554 kmod_search_moddep: could not  open moddep file '/lib/modules/3.13.0-24-generic/modules.dep.bin'



Please see these results and help.


Thank You Vary Much...

---

### Post by Hadaka on 2014-05-10
hi, are you able to use the wired connection?
if so..please do..
```
sudo apt-get install linux-headers-generic
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
thanks.

---

### Post by Varun_C on 2014-05-12
Tried with a wired connection
The result is same.. 

Code:
sudo modprobe b43

Result:
libkmod: ERROR ../libkmod/libkmod.c:554 kmod_search_moddep: could not open moddep file '/lib/modules/3.13.0-24-generic/modules.dep.bin'

Thinking to install Ubuntu 14.04

Please advise .


Thanking You...

---

### Post by Hadaka on 2014-05-12
Hi Varun, it sounds like you may have a bad file on your image disc
the iso disc. 4318 is a simple easy driver to load. If you reload again
when  it asks...about a proprietary driver...or makes any offer to supply
a driver as in additional dirvers...say...NO
then.. simply load the correct driver..
```
sudo apt-get update
sudo apt-get  install linux-firmware-nonfree
sudo modprobe b43
```
thanks.

---

### Post by Varun_C on 2014-05-12
Thanks for the help..

I have installed a fresh Ubuntu 14.04 in my Desktop PC.
I have a wired internet connection shared from my laptop to the Desktop System.

Please give the instruction to install the driver 4318 (Broadcom). I don't want to try anything without your instructions.

Please help...

---

### Post by Hadaka on 2014-05-12
Hi Varun...the instructions are the same in post #8
you need to connect the ethernet and be on the internet
from a wired connection please do..
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by Varun_C on 2014-05-12
Its amazing..

Commands executed without any errors.
 Restarted the system.

Now WiFi is working fine..


thanks a lot   [ 						 					]("http://ubuntuforums.org/member.php?u=1599436") 				 				 					 						 	[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1599436_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1599436")[**[COLOR=#000000]Hadaka[/COLOR]**]("http://ubuntuforums.org/member.php?u=1599436")....


Thank you for the support..

Keep in touch for further assistances please...

---

### Post by Varun_C on 2014-05-12
its amazing..
All commands executed without any errors
Wireless working fine after restarting.

Thanks you very much for the support and patience..

Keep in touch [URL="http://ubuntuforums.org/member.php?u=1599436"] 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1599436_1.gif[/IMG]**[COLOR=#000000]Hadaka [/COLOR]**[COLOR=#000000]for future assistance as I am a biginner to Ubuntu..[/COLOR][COLOR=#000000] [/COLOR]
[/URL]

---

### Post by Hadaka on 2014-05-12
GREAT ! thank you for following instruction, that makes it easy.
please take the time to mark this thread SOLVED..
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

