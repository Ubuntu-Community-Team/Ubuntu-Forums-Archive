---
title: "TP-Link Router Can't Support Network Printer"
date: 2017-07-23
forum: Networking &amp; Wireless
---

### Post by hJrBzw3 on 2017-07-23
Our network setup is one Lubuntu machine (me) and two Windows machines (partner and my work computer). We have a TP-Link router and a Brother HL-1110 laser printer. The printer can communicate with my Lubuntu computer just fine; the problem is trying to set it up as a network printer. I'm sure it's a router-related problem but even following the guide on TP-Link's website to set up a network printer didn't fix it:

[http://www.tp-link.com/us/faq-352.html](http://www.tp-link.com/us/faq-352.html)

No matter where I have the device URI pointing, the printer status in the printer settings dialogue box is always "The printer is not responding." 

This setup worked fine with a different, older router (forget the make and model), right out of the box, which is why I think it's a router-related issue. What am I doing wrong?

---

### Post by johndough2 on 2017-07-24
Hi

Don't know that you are doing anything wrong.

So the printer has a FIXED IP address?

You can ping the printer from Lubuntu?

If so then start with a ping from the windows machines to Lubuntu and then printer.

Is the naming convention as per the guide, Printer Q = lp1 and ......
################################################
LPD/LPR (Line Printer Daemon/Line Printer Remote) printing is a type of printing connection most commonly used in Unix/Linux networks.  It can also be used by Windows as an alternative method of connecting workstations to the print server.  The main advantages are that it bypasses certain Windows Permissions issues that can occur in Workgroup setups, and it also allows the printer to be installed as a &#8216;Local Printer&#8217; on the workstation (Some specific Large format Printers and Applications require printing be done through a Local Printer).
#################################################

lpd://192.168.0.10/lp1

Have you considered the Internet Printing Protocol which is also usable by Windows/Unix/Linux etc. which seems to be available on the TP Link?

---

