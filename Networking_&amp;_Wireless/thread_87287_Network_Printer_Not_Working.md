---
title: "Network Printer Not Working"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by bkanuka on 2005-11-07
When I go into System -> Administration -> Printing  and try to add a network printer, It doesn't ever actually add the printer.  The cups printers.conf doesn't change and neither does the list on localhost:631 (No Printers).  I can add a fake local printer and that shows up in the Printers list.  I do have cups and samba installed.
Thanks

---

### Post by bkanuka on 2005-11-07
[Duplicate Post]

---

### Post by taurus on 2005-11-07
Does your network printer (brand and model) have a static IP or a dynamic IP?  I don't have any problem printing to our HP LaserJet 4200 across the hall from my office with a static IP.

---

### Post by bkanuka on 2005-11-07
The printer, an HP DeskJet 3650, is attached to a Windows 2000 computer with a static IP.  I tried setting *host* to both OFFICE (the name of the W2K computer) and 192.168.0.2 (its IP) neither work.
Just to help solve it, someone who does have a working printer in a setup similar to mine, try to add a Samba printer (through the System -> Administration -> Printing) with garbage in the entries for host and printer name and tell me if it shows up in the Printers window.  That way I will know if it there is a problem with my Ubuntu computer.  If you don't understand, you can still help by just doing it; sometimes I have trouble explaining myself.
Thank you very much for any help.

---

### Post by bkanuka on 2005-11-09
.....bumping.....

---

### Post by dannemil on 2005-11-11
[QUOTE=bkanuka]The printer, an HP DeskJet 3650, is attached to a Windows 2000 computer with a static IP.  I tried setting *host* to both OFFICE (the name of the W2K computer) and 192.168.0.2 (its IP) neither work.
Just to help solve it, someone who does have a working printer in a setup similar to mine, try to add a Samba printer (through the System -> Administration -> Printing) with garbage in the entries for host and printer name and tell me if it shows up in the Printers window.  That way I will know if it there is a problem with my Ubuntu computer.  If you don't understand, you can still help by just doing it; sometimes I have trouble explaining myself.
Thank you very much for any help.[/QUOTE]

Are you sure that the firewall on the Windows 2000 computer is set to allow you to access that printer? I had trouble printing to a Windows XP printer until we allowed my IP Address as an exception to be able to access the printer with a username and password.

---

