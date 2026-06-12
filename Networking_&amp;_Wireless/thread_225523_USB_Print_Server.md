---
title: "USB Print Server"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by grj on 2006-07-29
I have a Linksys psus4 print server that I cannot make work with my Ubuntu laptop. I installed the server version, then added Xorg, CUPS and ion3. I cannot print.

Any help in this area would be welcome.

Also, does anyone have a print server for a usb printer that they have working well?

---

### Post by jay_atienza on 2006-08-12
Mine works just fine.  Setup is Linksys PSUS4 print server w/ usb Epson Stylus Photo R300.
Added a new printer: Unix Printer (LPD)
Host = Server IP address (192.168.x.xxx)
Queue = L1

---

### Post by momist on 2008-06-17
> **jay_atienza said:**
> Mine works just fine.  Setup is Linksys PSUS4 print server w/ usb Epson Stylus Photo R300.
Added a new printer: Unix Printer (LPD)
Host = Server IP address (192.168.x.xxx)
Queue = L1

Hi Jay, 
It's the little things that trip me up.  LPD doesn't mean a great deal to me, and I wouldn't have known about L1 for the queue.  
Thanks for the pointers, this post has made my print server work!

Ian

---

