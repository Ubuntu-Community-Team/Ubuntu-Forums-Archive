---
title: "Ubuntu 8.10(intrepid) - Troubles with ndiswrapper"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by fubarista on 2008-11-14
I just converted to Ubuntu from an obscure source-based distro and am really enjoying Ubuntu's user friendliness, documentation, and package management system. That said, I can't get my wireless working!


My card is a D-Link DWL-G510 with a Marvell W8300 chipset. Its PCI id (as given by lspci -nn) is as follows:

[FONT="Courier New"]01:0a.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter [11ab:1fa6] (rev 07)[/FONT]



I downloaded the proper drivers and installed them successfully in ndiswrapper:

[FONT="Courier New"]fubarista@host:~$ ndiswrapper -l
mrv8k51 : driver installed
	device (11AB:1FA6) present[/FONT]



Modprobing ndiswrapper gives me the interface wlan1. I can detect networks using "iwlist wlan1 scan", but cannot connect. Regardless of their level of encryption. Attempting to do so gives the following error in /var/log/messages:

[FONT="Courier New"]Nov 14 13:45:49 host kernel: [ 2327.162493] ndiswrapper (set_essid:59): setting essid failed (C0000001)[/FONT]



When I follow the same steps, for the same network, in another distro (i.e. a knoppix livecd), ndiswrapper gives me an interface that works just fine. Any ideas about what breaks it in Ubuntu and how to fix it?

---

### Post by jtdelasalas on 2008-11-15
I overcame this issue by running these in the terminal

sudo rmmod ndiswrapper; sudo rmmod b43; sudo rmmod ssb

then 

sudo modprobe ndiswrapper; sudo modprobe ssb

my wireless card then picked up everything

hope this works, so far i have to do this each time i restart

---

### Post by superprash2003 on 2008-11-15
does it connect to an unsecure network?

---

### Post by jtdelasalas on 2008-11-15
My home wireless network is secured and that method worked for me.

---

