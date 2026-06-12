---
title: "Samba Print Server connect Ethernet Laser Printer"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by Kevin_Rook on 2014-03-17
Hi,

I really need some help with Samba,

im running Ubuntu Server, and have installed Samba4.

I have the samba file sharing working fine across the network.

i've followed several tutorials on how to add a printer to be shared. so in windows i can see a ricoh c2030 Laser printer shared. but my problem is i think the tutorials set up based on a wired printer to the server, creating a spool in samba etc.

but my laser printer connects directly to the network switch. and has an IP address of 10.1.0.212

the server IP is 10.1.0.237

how do i tell samba that my printer has an ip address so it can see the printer? as its not connected via lpt or usb.

i have attached a txt file copy of my smb.conf as it is now...  the [Queue1] is a mess now as i've been trying to add the ip address of the printer.

[ATTACH]251229[/ATTACH]

Regards

Kevin

---

