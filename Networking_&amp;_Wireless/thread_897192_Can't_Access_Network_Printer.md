---
title: "Can't Access Network Printer"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by klausner on 2008-08-21
I connected a HP Photosmart 2600 printer via a Buffalo LPV3-U2 USB network print server. I can see and ping the printer at 10.10.10.11, and I can print to it over the network from a Windoze box, but not from a Linux box running Hardy, 8.04.

I've tried installing and re-installing the printer several times. If I install through the gnome-cups-manager app, I get an error of  job-hold-until-specified when I attempt to print. If I install from [http://localhost:631](http://localhost:631), I get "recoverable: Network host '10.10.10.11' is busy; will retry in *xx* seconds...".

The URI is set as ipp://10.10.10.11, the driver is hpijs, and I've tried the device as ipp, LPD/LPR, HPLIP (which reverted to ipp), and SAMBA (which also reverts to ipp), with no success.

How do I get this to work from Linux?:(

---

### Post by klausner on 2008-08-21
After posting the previous, I decided to make sure that the problem wasn't something stupid like the printer being off-line. In thumbing through the printer's menus, I was mildly surprised ot see "Network Settings" as a choice. I've had this printer for ~four years, and hadn't looked at the connections in the back since I installed it. :redface:

I moved the printer from the wall, and pulled out the cover concealing the RJ-45 jack. I disconnected the USB server, and used that network cable to connect directly to the printer.

I ran the gnome-cups-manager app, and removed the latest install of the HP. When I then went to add a printer, it immediately saw and recognized the HP, and had no problem printing a test page.

So I still don't know why the Buffalo LPV3-U2 didn't work, but kudos to HP for idiot-proofing the hardware.

---

