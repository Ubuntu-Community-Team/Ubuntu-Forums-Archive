---
title: "unable to locate wireless hardware on device"
date: 2014-12-25
forum: Networking &amp; Wireless
---

### Post by RogerDavis on 2014-12-25
I'm tryhing to get wireless printing working with Ubuntu 14.04 and a HP LaserJet Pro printer, model MFP M177fw.

The best result I can get is "unable to locate wireless hardware on device".  I have no idea if this means the printer or the computer.

The desktop (which I am using to setup) has no wireless.  It's connected by  USB.  The laptop in the other room has wireless.

Help?

---

### Post by Bucky Ball on 2014-12-25
You generally need to set the printer up via USB first. Set a static IP address on the printer, etc. Have you got HPLip installed? That is in the repos. If not, install. Plug the printer in via USB and get it connected, set it up that way. Once it's working via USB, unplug and get to the wireless side.

You can open a web browser and in the address bar type 'localhost:631'. That should give you the cups interface. Or you can use the 'Printing' option of Ubuntu and 'Add' printer>Network Printer. Give it awhile to search. Your printer should show up. Select the appropriate driver for your model when you get there.

---

### Post by RogerDavis on 2014-12-25
The printer is set up and working for a few weeks on the desktop.  I have HPLip and the Toolbox installed.  Is it necessary to disconnect the USB from the desktop, when it's the laptop in the other room I want to connect?  

I presume the instructions you show for the browser are for use with the laptop?  I've tried to set up the printer on the laptop, and having a great deal of problems in device discovery, using several different ways.  Do I need to connect the laptop by USB to get this done?

---

### Post by Bucky Ball on 2014-12-25
Well, you need to set up the printer on the computer you have it connected to via USB and set a static IP address to start.

---

### Post by RogerDavis on 2014-12-26
OK, got it set up using the USB on the desktop.   Works fine from the desktop.   So I guess the static IP is to be set on the printer.  IP on printer now shows 0.0.0.0  If this isn't right, how do I change it?  And then what do I do with it?

It keeps asking for a plugin, but I have successfully installed it twice - requires proprietary plugin (color, 2-sided printing)

I find all this under the printer side of the CUPS Modify Printer setup from the USB desktop, not the wireless laptop that I want to set up : 
Modify HP_Color_LaserJet_Pro_MFP_M177fw
Current Connection: 	hp:/usb/HP_Color_LaserJet_Pro_MFP_M177fw?serial=CNB6FDDFPL
Local Printers: 	Serial Port #5
HP Color LaserJet Pro MFP M177fw (HP Color LaserJet Pro MFP M177fw)
HP Color LaserJet Pro MFP M177fw USB CNB6FDDFPL HPLIP (HP Color LaserJet Pro MFP M177fw)
HP Color LaserJet Pro MFP M177fw USB CNB6FDDFPL HP Fax HPLIP (HP Fax 2)
Discovered Network Printers: 	
Other Network Printers: 	Internet Printing Protocol (https)
Internet Printing Protocol (ipp14)
Internet Printing Protocol (http)
Internet Printing Protocol (ipps)
AppSocket/HP JetDirect
Internet Printing Protocol (ipp)
Windows Printer via SAMBA
LPD/LPR Host or Printer

---

### Post by Bucky Ball on 2014-12-26
Your printer IP should be something like 192.168.0.100, as long as nothing else is using that IP already. You need to check the router settings here and ascertain the range it is serving IP addresses in and limit it. For instance, limit the range the IP is serving IP addresses in to 192.168.0.10 - 192.168.0.20 and make the static IP for the printer 192.168.0.21. This way, there can be no conflict.

Without knowing the exact setup of your router's DHCP server, it is hard to give specifics.

Once you have the IP setup on the printer, then go to the laptop (or the machine you want to connect to it wirelessly) and add the network printer.

---

### Post by RogerDavis on 2014-12-26
All works now.  Simple, just need to enter the correct password (damn 23 character passwords in microscopic print), then it was all automatic.

---

### Post by Bucky Ball on 2014-12-27
Great news and thanks for marking as solved. ;)

---

