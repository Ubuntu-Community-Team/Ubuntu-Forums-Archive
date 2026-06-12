---
title: "lubuntu 16.04 samba shares and printer only with DHCP - not static IP"
date: 2016-06-22
forum: Networking &amp; Wireless
---

### Post by jpantone on 2016-06-22
Title says it all.
I can find and install my network printer (shared via SAMBA from a NAS) and share my Public directory, but only if I use DHCP
can't set the IP manually (static).

With DHCP assigning IPs on CINNAMON, I get:

[FONT=Courier New]
john@cinnamon:~$ smbtree -N
WORKGROUP
	\\NANCYS-PC      		
GRIZZLYNET
	\\CO-NAS         		Home Media Network Hard Drive
		\\CO-NAS\Backups        	
		\\CO-NAS\Documents      	
		\\CO-NAS\Movies         	
		\\CO-NAS\Music          	
		\\CO-NAS\Pictures       	
		\\CO-NAS\QuickTransfer  	
		\\CO-NAS\HPPhotosmartC5500series	HPPhotosmartC5500series
		\\CO-NAS\IPC$           	IPC Service (Home Media Network Hard Drive)
	\\CINNAMON       		cinnamon server (Samba, Ubuntu)
		\\CINNAMON\HPPhotosmartC5500series	HPPhotosmartC5500series
		\\CINNAMON\IPC$           	IPC Service (cinnamon server (Samba, Ubuntu))
		\\CINNAMON\Public         	
		\\CINNAMON\print$         	Printer Drivers
	\\BLACKBEAR      		blackbear server (Samba, Ubuntu)
		\\BLACKBEAR\Public         	
		\\BLACKBEAR\HP-Photosmart-c5500-2	CO-HP-Photosmart
		\\BLACKBEAR\IPC$           	IPC Service (blackbear server (Samba, Ubuntu))
		\\BLACKBEAR\print$         	Printer Drivers
john@cinnamon:~$ [/FONT]

And I can find and install the CO-NAS printer via SAMBA share

with CINNAMON set to static IP (192.168.0.150), the network disappears, can't find printer, and other systems can't see CINNAMON.

---

### Post by jpantone on 2016-06-23
Apparently this is a "known problem" - the only answer (get around) I've seen is to use DHCP, but to get the DHCP server to give a permanent lease to a particular IP/MAC address combination.

I have done this, and samba continues to work "normally".

This isn't really an answer, I think. Why would samba work differently for static and DHCP ?

---

