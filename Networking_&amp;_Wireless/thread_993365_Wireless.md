---
title: "Wireless"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by timmy__k on 2008-11-25
Hey folks,....I have read the tut on ndiswrapper, trying to get my wireless to work...I have had it working before, but system became unstable, and i lost my patience, did clean install.

Now no wireless...

ndiswrapper -l 

Then tried to install it...any suggestions??


timmyk@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
timmyk@ubuntu:~$ sudo aptitude install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "ndiswrapper-common"
Couldn't find any package whose name or description matched "ndiswrapper-common"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

as i read i saw maybe this output could be helpful
lspci -nn

01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

---

### Post by Ayuthia on 2008-11-25
> **timmy__k said:**
> Hey folks,....I have read the tut on ndiswrapper, trying to get my wireless to work...I have had it working before, but system became unstable, and i lost my patience, did clean install.

Now no wireless...

ndiswrapper -l 

Then tried to install it...any suggestions??


timmyk@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
timmyk@ubuntu:~$ sudo aptitude install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "ndiswrapper-common"
Couldn't find any package whose name or description matched "ndiswrapper-common"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

as i read i saw maybe this output could be helpful
lspci -nn

01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

If you are using Intrepid (8.10), go into System->Administration->Hardware Drivers and activate Broadcom STA.  It is the proprietary driver made by Broadcom, but it should get you connected to the internet.

---

### Post by timmy__k on 2008-11-25
I went there, and the option i have there is 

nvidia_new which im assuming is my graphics/chipset .....not 100%

---

### Post by Ayuthia on 2008-11-25
> **timmy__k said:**
> I went there, and the option i have there is 

nvidia_new which im assuming is my graphics/chipset .....not 100%

Please try the following:
```
sudo updatedb
locate wl.ko
```
The first command should run for a little bit.  It is updating the search database.  The second command should return the location of the Broadcom STA driver.  If it is not there, please do the following:
```
sudo /etc/init.d/linux-restricted-modules-common start
ls /lib/modules/`uname -r`/volatile
sudo depmod -a
```
The first command should come up with an ok and then the second command hopefully will bring up the wl.ko module.  The third command will update the dependencies for the kernel modules.  If the second command shows the wl.ko file, you can do the following:
```
sudo modprobe wl
```Wait a few seconds and you should be able to connect.

Hope that helps.

---

### Post by timmy__k on 2008-11-25
i get nothing i type "sudo updatedb" and it goes right back to my ...

timmyk@ubuntu:~$ sudo updatedb
timmyk@ubuntu:~$

---

### Post by Ayuthia on 2008-11-25
> **timmy__k said:**
> i get nothing i type "sudo updatedb" and it goes right back to my ...

timmyk@ubuntu:~$ sudo updatedb
timmyk@ubuntu:~$

Sorry.  If the command works, it does not return anything.  Go ahead to the next steps.

---

