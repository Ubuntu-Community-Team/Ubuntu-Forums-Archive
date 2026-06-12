---
title: "cannot get wireless working"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by SDracul on 2006-11-09
I have searched thru the forum and found a link to this page [http://doc.gwos.org/index.php/HowToDWLG122](http://doc.gwos.org/index.php/HowToDWLG122) I followed the instructions exactly.

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ndiswrapper-utils

cd Desktop
sudo ndiswrapper -i "PRISMA02.inf" <- (from the dwl-g122 cd the prisma02.sys from the xp directory of the cd was on the desktop also)
sudo modprobe ndiswrapper
sudo ndiswrapper -m

gksudo gedit /etc/network/interfaces

added this to the end of the file

auto wlan0 <- this line was already in the file the lines below I added
iface wlan0 inet dhcp
wireless-essid my ssid here
wireless_mode managed

When I typed sudo modprobe ndiswrapper
I reveived an error - Error inserting ndiswrapper (/lib/modules/2.6.17.10-generic/kernel/drivers/ndiswrapper/ndiswrapper.ko): Invalid Argument

Since I just installed Ubuntu 6.10 today I am not quite sure about the error. 
I have a usb Dlink DWL-G122.


I have no lights on my DWL-G122 and only have the wired connection and modem in the Network window. Could someone please help me out with this - I would like to change all my computers to Ubuntu but I really need the wireless on a few of them. Thank you.

---

### Post by maxwellcom on 2006-11-11
SDracul:

I am having the same exact problems... if you find the solution please post.  I'm looking, and will do the same.

Thanks,
Nathan

---

### Post by maxwellcom on 2006-11-11
SDracul,

I managed to get at least past the error you are describing.  Here is what I did:

1. open System-> Administration->Synaptic Package Manager
2. search for ndiswrapper
3. mark any ndiswrapper-common and ndiswrapper-utils for complete removal
4. once uninstalled, search for ndiswrapper again and mark v. 1.18 of ndiswrapper-utils and ndiswrapper-common for installation
5. once installed, follow the steps of the howto you referred to again.  it should work this time.

hope that helps.

---

### Post by SDracul on 2006-11-12
That is something similar to what I did today to get it working. 
Basically I uninstalled everything to do with ndiswrapper thru terminal

sudo modprobe -r ndiswrapper
sudo apt-get --purge remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper


then typed the following in terminal
 
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /home/dracul/Desktop/prism02.inf
sudo ndiswrapper -l 
sudo modprobe ndiswrapper <- light on my usb dongle blinked once

Then I went into Network and the wireless icon wlan0 was there so I was able to then add the info for my network.

Then I typed in terminal

sudo ndiswrapper -m
gksudo gedit /etc/modules

and added the following to the module list
ndiswrapper

This will load ndiswrapper on start up.

I hope this helps anyone who is having the same problem.
Next is windows shared directories.

---

### Post by robli99 on 2006-11-12
I followed your instructions, step-by-step, but it does not work.
sudo modprobe ndiswrapper <- the light didn't blink at all. The first time I installed it, it blinked once. But it never light up after I restart the pc, even after I re-install it totally.
The driver works well in FC5 before I turned to Ubuntu 2 weeks ago.

---

