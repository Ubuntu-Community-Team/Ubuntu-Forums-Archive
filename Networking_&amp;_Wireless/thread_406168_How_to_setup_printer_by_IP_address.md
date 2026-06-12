---
title: "How to setup printer by IP address?"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by wraith0078 on 2007-04-10
Okay, I've managed to connect and authenticate to my Active Directory domain and now I want to setup a network printer, preferably by IP address.  What do I need to do this?

---

### Post by amitst on 2007-04-11
I have successfully added an HP network printer using the following method (maybe helpful to you).
- System -> Administration -> Printing
- Add Printer
- Select Network printer and select 'HP jetDirect' in the dropdown
- Give IP in the Host, keep port as 9100
- Select printer model
That's it

---

### Post by BillinDetroit on 2007-04-11
I've been away from Linux for a couple of years so my answer may be a little rusty, but I got my printer (Ubuntu 6.10 running in a VirtualBox VM on XP) to print after only a few minutes fiddling around.

Your entry will take the form of 
[http://IPaddress:port/printername](http://IPaddress:port/printername)
viz 
[http://192.168.1.5:631/EPSON_IPP_Printer](http://192.168.1.5:631/EPSON_IPP_Printer) 

Check the printer installation docs for the exact address. You may also get the address from a Windows machine sharing the same printer. 

Hopefully helpful,
Bill

---

