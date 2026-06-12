---
title: "configuring network printers: help needed.."
date: 2005-05-09
forum: Networking &amp; Wireless
---

### Post by ash on 2005-05-09
Hi, 

Have replaced Windows XP with Hoary Hedgehog, would like to install 2 network printer (HP 2300dn and HP Laserjet 6P). 

These are printers shared between computers on the University ethernet from which I connect to the net.  

In XP it was possible to install by going to Add Printers, then creating a new parallel port (TCP/IP),giving the port IP address, and finally installing the printer driver. 

What is a similar process in Ubuntu? 

Please treat as complete newbie... help would be greatly appreciated :) 

Thanks, 
Ash.

---

### Post by dataw0lf on 2005-05-10
In Gnome : 
System -> Administration -> Printing -> Printer -> Add Printer

---

### Post by ash on 2005-05-10
[QUOTE=dataw0lf]In Gnome : 
System -> Administration -> Printing -> Printer -> Add Printer[/QUOTE]

Thanks, got it...
ok, in XP I used to install the printer by creating a new parallel port, then I would be asked for the port address, but here there seems to be no such dialog. Is there something I am missing? 

Thanks, 
Ash.

---

### Post by Staesys on 2005-05-11
Try sellecting Unix printer (lpd) and entering the ip address in the first box, and the port name in the second box. For my printserver that's something like:

192.168.2.200
PS-PORT_1

Hope this helps!

-Paul

---

