---
title: "Trouble installing Linksys/Broadcom driver via ndiswrapper"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by taosaur on 2007-01-21
After more hours of fiddling than I'd like to admit, I'm making zero headway installing my Linksys WPC54GS (speedbooster) card in Edgy.  

fw-cutter for firmware (found to work on UK version with same chipset) did not work.  Instructions at sourceforge and the ubuntu forums & wikis for installing ndiswrapper were incomplete and unintelligible.  

Finally I found [_these instructions_]("http://www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php") for Breezy, which supposedly worked for others in Edgy.  Here are the results of this attempt: > ~$ sudo ndiswrapper -i /cdrom/lsbcmnds.inf
Installing lsbcmnds
cp: cannot stat `/cdrom/lsbcmnds.inf': No such file or directory
~$ sudo ndiswrapper -i /cdrom/Drivers/9x/lsbcmnds.inf
lsbcmnds is already installed. Use -e to remove it
~$ ndiswrapper -l
Installed ndis drivers:
lsbcmnds        invalid driver!
~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
~$ sudo depmod -a
~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

Any idea what when wrong here, or what I can do to fix it?  Do I need to undo any of this, and if so how?

My next step is to try downloading the driver from Linksys rather than lift it from the cdrom, and try again.

---

### Post by teaker1s on 2007-01-21
[COLOR="Red"]sudo apt-get install ndiswrapper-utils-1.8[/COLOR]

---

### Post by taosaur on 2007-01-21
I solved my problem using [this excellent thread]("http://ubuntuforums.org/showthread.php?t=185174"), with detailed instructions and troubleshooting for installing the bcm43xx driver and extracting the firmware.  I first completely removed ndiswrapper-utils with Synaptic Package Manager.  I also had to blacklist ndiswrapper (some quirk of the 4318 chipset), and replace Network Manager with Wifi Radar.  

I wish the 43xx thread were stickied in this forum rather than buried in another :roll:

---

