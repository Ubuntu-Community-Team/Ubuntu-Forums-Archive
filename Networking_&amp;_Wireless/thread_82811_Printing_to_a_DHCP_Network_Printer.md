---
title: "Printing to a DHCP Network Printer"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by Leadherent on 2005-10-27
Hi, 

I am a new member to this group. I live in Finland. Currently I am doing my thesis on computer aided music notation. I do most of my work on OS X and some in XP. Recently I installed Ubuntu on a Siemens laptop which also hosts XP (BTW, Ubuntu runs very nice, no problems with install or coinciding with XP). However, I have very little knowledge on Linux and this brings me to my question :-)

I have a small home network with a LAN printer and mac (10.4), xp, and ubuntu boxes connected (via a switch) to the internet. My service provider serves (DHCP) IP addressed to all the machines in my network, including the printer. The printer is a HP 2100M with a JetDirect card for networking. 

All the machines can access the www fine, and I can print from OS X to my printer. I can also connect the xp and mac boxes to do some file sharing etc. 

My problem is that, apart from figuring out the dynamic IP address of the printer, I have not been able to create a printer setup in Ubuntu so that it would automatically detect the HP's changing address as, for example, OS X does.

Can this be done? What would be the best way to get all the OSes to see the printer.

Best Regards,

L

---

### Post by davmac on 2005-10-27
It is not something I've had to do myself but there's a good white paper available (PDF) about Linux Network Printing with JetDirect at [http://portal.dfpug.de/dFPUG/Dokumente/Partner/Linuxtransfer/networking_linuxnetworkprintingwithjetdirect.pdf](http://portal.dfpug.de/dFPUG/Dokumente/Partner/Linuxtransfer/networking_linuxnetworkprintingwithjetdirect.pdf)

HTH,

Dave Mac

---

### Post by Leadherent on 2005-10-27
Hi Dave,

The paper was an interesting reading but I could not find a solution to my problem there :sad:. But thanks anyway...

Regards,

L

---

### Post by byourg on 2005-10-27
If the HP printer has a network name eg. \\HP JETDIRECT, use that for a host in the Ubuntu printer settings instead of IP address.

---

### Post by Leadherent on 2005-10-28
Is network name the same as hostname? That I could find. I could not get anything work, however. The cups admin of OS X detects the printer but Ubuntus does not...

Regards,

L

---

### Post by davmac on 2005-10-28
Can you set the hostname of the printer? If so when adding the printer you should be able to give the address as http://<hostname>:631/printers/<printername>

Dave Mac

---

