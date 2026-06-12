---
title: "hplip, one printer shows up, other doesn't"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by Mateo on 2007-01-09
I have two printers hooked up to my network.  One is a deskjet all-in-one and the other a laserjet.  The deskjet shows up fine, got installed using the instructions on the website, almost no problem (i haven't tried all of the features yet, but so far so good).  But the laserjet doesn't even appear.

The thing is, if I go into my router, the laserjet doesn't even appear on the network.  Why could this be?  It's hooked up, and works on all of my computers with XP.  Why doesn't it appear on the network?  Is there something else I need to do to get the printer to show up on the network?

---

### Post by Mateo on 2007-01-09
bump.  if someone could just point me in the right direction for why the printer isn't show up as part of the network when I look at my router's tables, that would be a good start.  and again, the printer *does* work on my computers with windows (including this one).  but it still never shows up on the network.

---

### Post by 11hjpphty76lkjj on 2007-01-12
Can you ping the laser printer from your linux system?

A

---

### Post by Mateo on 2007-01-12
not sure, could you tell me how to do that?  Don't you have to have an IP address to ping?  I don't know what the IP address for the laser printer, like I said, because it doesn't show up on my router (even though it's hooked up to the router).

---

### Post by 11hjpphty76lkjj on 2007-01-12
Oh I see.  So the printer is connected the router and the router isn't giving the laserprinter an IP address.  It should show you in the router the IP address.  Or you can select some options on the printer to print out the network config page.  If the printer isn't getting an IP then perhaps there is a  configuration problem on the printer. 

Sorry this doesn't help more.

A

---

### Post by Mateo on 2007-01-12
ok, I found out what it was.  i looked at my laptop (which has windows and the printer already installed and working) and found under some settings that the printer name is NPIBFA666.  I typed that into the browser and discovered that the IP address is 192.168.1.100.  i'm going to log onto linux and see if this information helps me install the printer.  i'll get back.

---

### Post by Mateo on 2007-01-12
Yep, worked just fine once I manually put the IP into the New Device wizard.  For some reason I had convinced myself that because it wasn't (and still isn't) showing up on the router's page, that it must not be installed on the network properly.  I didn't even think to look on one of my windows computers to see if I could figure out the IP address.  Once I found that, it was easy.

Good piece of drivers/software.  Probably the best in terms of working flawlessly with the hardware in question.  My officejet all-in-one does everything that i want, prints, scans, copies of course.  I haven't tried fax but I never use that anyways.

---

### Post by 11hjpphty76lkjj on 2007-01-12
Great! :-D

A

---

