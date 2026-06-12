---
title: "[SOLVED] Wireless Print server and installation repair"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Anna Graham on 2009-01-08
I've spent the past day trying to tweak my non-Wubi Ubuntu install into seeing a printer on a wireless print server. This worked fine in WUBI (in XP PRO) where System > Admin > Printing discovered the printer immediately.

So the non-Wubi install wouldn't see it. I did everything (a mistake) the forums suggested. I can ping the printer. I can access the print server via a web interface. But nothing in the printer selection. At this point I'm admitting defeat and asking for help on two issues:

1) Printer: I have a netgear WPN824 wireless router. I have a WGPS606 wireless print server connected to the router via the ether. I've an epson CX4200 attached to L1 (a usb) on the print server. This configuration worker fine for XP and a MAC laptop. It didn't seem to be an issue for Wubi. So how do I make it happen in full Ubuntu 8.10 install? Why was it a non-issue in Wubi>

2) I have probably screwed up the install during this process. At first, the print drivers were available as I followed the add new printer instructions (to no avail). Now they are gone, probably during an uninstall/reinstall of CUPSYS. So how to I revert back to a clean install of 8.10? I am only a few days into the non-Wubi install. Is it just a reformat/reinstall? Is there a repair option? Or do I just shake the box like my etch-a-sketch?

I am new at this. If I need to supply more info (say from a terminal command) be precise and a something I could cut and paste would be great. If I need to obtain a package to run in terminal, a link to that would be good.

---

### Post by Anna Graham on 2009-01-09
Alright. Both questions answered:

1) Wireless configuration: downloaded the guide for WGPS606 print server install on a MAC 

<http://kbserver.netgear.com/inquira/default.asp?ui_mode=answer&prior_transaction_id=7727&action_code=5&highlight_info=16777350,17,36&turl=http%3A%2F%2Fkbserver.netgear.com%2Fkb_web_files%2FN101570.asp&answer_id=358700#__highlight>

and used those instructions as a guide:
Protocol: LPD
Address: xxx.xxx.x.xxx (print server IP)
Queue: L1

Installed the drivers and got the thing to work. Since it's behind a wireless router, I'm thinking the static IP address concern might not be a problem until the router powers down. But at least I got the main problem solved.

2) Fresh Install: just booted up the install disk and asked for the install.

Hope this helps someone else.

---

### Post by handydan918 on 2009-01-09
> **Anna Graham said:**
>  Since it's behind a wireless router, I'm thinking the static IP address concern might not be a problem until the router powers down. 


Most routers have an option to "reserve" an IP address to a particular MAC address, but still do it via dhcp. I use it. All the advantages of dhcp, and fixed IPs, too.

---

