---
title: "BCM4301 in Feisty. Can't get it to work."
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by loveshackdave on 2007-04-22
So I've looked at all of the tutorials, tried the firmware method, tried ndiswrapper and nothing seems to work. I even tried getting the wireless card to work in Edgy (via ndiswrapper) and then doing a dist-upgrade. This didn't work either ;P. need some help!! Here is what I am doing with ndiswrapper:

sudo rmmod bcm43xx
sudo ndiswrapper -i <drivers that work under edgy>
sudo ndiswrapper -l (tells me that hardware is present and drivers are present)
sudo modprobe ndiswrapper 
sudo ndiswrapper -m

at this point my wireless card (eth1) is not showing up anymore in iwconfig and I have no wireless connectivity. What am I missing? This was so easy in Edgy.

---

### Post by revmc on 2007-04-22
I usually do the following in addition to what you have done.

gksu gedit /etc/modprobe.d/blacklist  and type blacklist bcm43xx and then save

gksu gedit /etc/modules and add the word ndiswrapper

gksu gedit /etc/network/interfaces and make sure there is no eth1, if so change to wlan0

gksu gedit /etc/iftab and change eth1 to wlan0

restart

---

### Post by luisromangz on 2007-04-22
I'm using Feisty now with the bc43xx drivers and my broadcom wireless card works flawlessly. While doing dist-upgrade, it automagically downloaded the firmware. If you have no luck and want to stick with ndiswrapper, you should check that you have blacklisted bcm43xx driver by adding it to /etc/modprobe.d/blacklist as the previous poster said.

Good luck!

---

### Post by itsmeagain on 2007-04-22
Hi had similar problems, worked all day on it and now it works fine apart from it does not like WEP, try what I did, it may be a bit long winded but it worked for me. Note: you may need a different Windows driver to what i used.

Ubuntu Feisty 
Wireless Card Set-up Instructions using ndiswrapper

Wifi card ref:  Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02) 
ndiswrapper version:  ndiswrapper-1.42.tar.gz
Windows driver files needed: WMP11V27.inf and WMP11V27.sys

Disabling the default Windows driver
The Wifi driver supplied with Ubuntu Feisty (bcm43xx) did not work with my wireless card so I disabled it.

Disabling bcm43xx driver...
Open a terminal by going to Applications > Accessories > Terminal
Code:
sudo rmmod bcm43xx
Input the root password if prompted 

Editing the blacklist file...
Code:
sudo gedit /etc/modprobe.d/blacklist
Actions... Add to the bottom of the file “blacklist bcm43xx” > Save the file and close the window

Installing ndiswrapper...
To install ndiswrapper we need firstly to have two programs installed in Ubuntu,,  “kernel-headers”and “build-essential”. Luckily the “kernel-headers” are installed by default so we only need to install “build-essential”

Installing “build essential”...
Insert the Ubuntu installation CD > in the windows that opens click on “Start package manager” > this opens the “Synaptic Package Manager” window > in the Search window type in “build-essential” > Search > you will see the “build-essential” program > mark it for installation and then install it > once installed close Synaptic Package Manager

Installing ndiswrapper...
Open a Terminal window > cd to the folder that contains ndiswrapper-1.42.tar.gz
Code:
tar xvfz ndiswrapper-1.42.tar.gz
This will create a folder named “ndiswrapper-1.42”, cd to this folder
Code:
make
Note: no errors should be seen
Code:
sudo make install
Input the root password if prompted

Installing the Windows driver {WMP11V27.inf}...
Using a Terminal cd to the folder where the file “WMP11V27.inf “ is located
Code:
sudo ndiswrapper -i WMP11V27.inf	
		
To list drivers installed...
Code:
sudo ndiswrapper -l					
report...
wmp11v27 : driver installed
	device  (14E4: 4301) present (alternative  driver : bcm43xx)

Update modules...
Code: 
sudo depmod -a

Test ndis modlule...
Code: 
sudo modprobe ndiswrapper

Initiate ndiswrapper as a system start-up module...
sudo ndiswrapper -m
report...
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

Modifying some files...
From a Terminal window
Code:
sudo gedit /etc/iftab
report...
# This file assigns persistent names to network interfaces. 
# See iftab(5) for syntax. 

eth0 mac 00:06:25:1c:f3:d6 a

Change this file as shown below, then File > Save ***... (iftab) > Save > Replace > close the window

# This file assigns persistent names to network interfaces. 
# See iftab(5) for syntax. 

wlan0 mac 00:06:25:1c:f3:d6 arp 1
wlan0 mac 00:0c:41:a1:bc:1c arp 1
Notes: 
wlan0 mac 00:06:25:1c:f3:d6 arp 1 is the Linksys wireless card mac address
wlan0 mac 00:0c:41:a1:bc:1c arp 1 is the Linksys router mac address
Without the router mac address there are problems and the wireless card does not work correctly



Code:
sudo gedit /etc/modules
report...
# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

fuse 
lp

Change this file as shown on the next page, then File > Save ***... (modules) > Save > Replace > close the window

# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

fuse 
lp 
ndiswrapper


Code:
sudo gedit /etc/modprobe.d/ndiswrapper
Report...
alias wlan0 ndiswrapper
Note:
This file should be OK

Reboot the machine

Setting up the Network...
Go to System > Administration > Networking > input the root password if prompted > click on Wireless Connection > Properties > set Network Name (ESSID):.  Configuration: to Automatic configuration (DHCP) > remove any tick from “Enable roaming connection”  > OK > Close

Checking one more file, it should look like below...
Code:
sudo gedit /etc/network/interfaces
Report...
auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet dhcp 
wireless-essid Homer 

auto eth1 
iface eth1 inet dhcp 

auto eth2 
iface eth2 inet dhcp 

auto ath0 
iface ath0 inet dhcp 

auto wlan0 
iface wlan0 inet dhcp 
wireless-essid Homer

let me know how you get on

Stew

---

### Post by loveshackdave on 2007-04-22
> **revmc said:**
> I usually do the following in addition to what you have done.

gksu gedit /etc/modprobe.d/blacklist  and type blacklist bcm43xx and then save

gksu gedit /etc/modules and add the word ndiswrapper

gksu gedit /etc/network/interfaces and make sure there is no eth1, if so change to wlan0

gksu gedit /etc/iftab and change eth1 to wlan0

restart

I already did the blacklisting and adding ndiswrapper to modules. I just forgot to mention it above. As for changing eth1 to wlan0, I didn't think it mattered as it is just a name. I did this though and it still does not work. Any other ideas?

Also, once I do the rmmod and blacklist bcm43xx, there is no longer a "Wireless Connection" option in the network manager

---

### Post by itsmeagain on 2007-04-22
Are you using WEP

---

### Post by loveshackdave on 2007-04-22
> **itsmeagain said:**
> Are you using WEP

no

---

### Post by itsmeagain on 2007-04-22
Have you got ndiswrapper installed

---

### Post by loveshackdave on 2007-04-22
> **itsmeagain said:**
> Have you got ndiswrapper installed

yes, it is configured as stated above. ndiswrapper -l reports that the driver is installed and hardware present. The same configuration works fine in Edgy

---

### Post by itsmeagain on 2007-04-22
Ok 
There is one command that you have not mentioned, have you done it?
code:
sudo depmod -a

---

### Post by loveshackdave on 2007-04-22
> **itsmeagain said:**
> Ok 
There is one command that you have not mentioned, have you done it?
code:
sudo depmod -a

yes I have done this.

---

### Post by bestiarosa on 2007-07-29
That worked for me... I just had to change wlan0 into wlan1. Thanks!

---

