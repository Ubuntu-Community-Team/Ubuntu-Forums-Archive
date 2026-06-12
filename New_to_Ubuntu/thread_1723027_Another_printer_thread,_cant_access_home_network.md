---
title: "Another printer thread, cant access home network"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by CWMV on 2011-04-06
So Ive just added Ubuntu to an old Vista based machine, still very new to it all.
Im trying to add my home network printer (cannon MP495) but cant do it through the add printer option.
System-Administration-printing-Add Printer-Network Printer-Windows Printer via Samba-Browse brings me to the SMB browser. I can see my home network, but when I select it the 'ok' button stays grayed out, preventing me from moving forward in adding the network/printer.

So...How the heck do I rectify this?

---

### Post by Wobblybob on 2011-04-07
Have you checked that your windows pc has shared the printer with the network and rebooted?

---

### Post by philinux on 2011-04-07
> **CWMV said:**
> So Ive just added Ubuntu to an old Vista based machine, still very new to it all.
Im trying to add my home network printer (cannon MP495) but cant do it through the add printer option.
System-Administration-printing-Add Printer-Network Printer-Windows Printer via Samba-Browse brings me to the SMB browser. I can see my home network, but when I select it the 'ok' button stays grayed out, preventing me from moving forward in adding the network/printer.

So...How the heck do I rectify this?

Open system>admin>printing and under the server tab make sure you have the tick boxes ticked that you need.

---

### Post by CWMV on 2011-04-07
Ya its shared, anyone who's hooked up to my home wifi network can use the printer. Heck I can 'see' it in the SMB bowser, just cant select it.
All appropriate boxes (that I'm aware of) are checked in settings.

---

### Post by Wobblybob on 2011-04-07
can you add the path to the printer in the box without using browse? If you can see the printer when you browse then you should know what windows has called it so you would add something like

workgroup_name/server-name:port_num/printer_name

my printer is on an ubuntu server so this is a bit of guess work but my wife Windows lappy sees it on port 631 so;

workgroup_name/server-name:631/printer_name

use the server name or ip address

Good Luck

---

