---
title: "Network printing from EDdgy 6.10 not working: HP 2605dn on Windows XP"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by cbourner on 2007-01-06
I have an HP 2605dn attached to a Windows XP machine via USB.  Another Windows machine can connect and print to it, so all is working there.

I have insttalled Edgy 6.10 on my notebook, and have wireless networking working well.  I can map shares on my Maxtor NAS unit using a mount command no problem.

I have tried to set up the printer as a network printer, identifying it as the correct model, and specifying the netbios name of the host PC, and the share name given to the printer.

Edgy says it is printing when I do a test print, but nothing prints.

I also noticed that the netbios name exists in the drop-down for the server, but when I use the drop-down for the available printers, the list is empty.

Is there something I need to install to make this work?  Any ideas anyone?

---

### Post by cbourner on 2007-01-08
Fixed!

Added PCs IP address to /etc/hosts.

I have an odd DNS issue which means changing nsswitch.conf to allow netbios names to be resolkved to an IP address doesn't work yet, but that can wait.

I can print!

---

