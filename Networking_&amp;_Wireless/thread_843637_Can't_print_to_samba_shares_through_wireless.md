---
title: "Can't print to samba shares through wireless"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by jgordon510 on 2008-06-28
I'm a teacher and in my classroom I've managed to share my windows desktop printer with my ubuntu laptop plugged into the school ethernet.  The URI looks like this:

smb://AUSD/RUB-303T/HPLaserJ

AUSD is the domain.  RUB-303T is my windows computer and HPLaserJ is the printer name.  It works great... as long as I'm plugged in with an ethernet cable.  

When I log onto my wireless router in my classroom, I can't access the same shared printer.  I can't browser the domain through Places -> Network.  Is there some router configuration?  Do i need to change the URI?  What can I do?  This would be huge for me so I wouldn't have to move my laptop from my digital projector in the center of the room to an ethernet port every time I want to print a document.

---

### Post by racin on 2008-06-28
I had the same problem this worked for me.
[http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html](http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html)

I found this in another thread.

---

### Post by jgordon510 on 2008-06-29
@Racin

That seems like it's just about configuring print sharing from a windows machine.  My problem seems not to be configuring, as it works through the wired connection but won't work through the wireless router.

---

### Post by racin on 2008-06-29
Hello,
Try setting it up like in the above post. I couldn't print from my wireless laptop to my XP machine since the Hardy upgrade. After I followed this procedure I can now print wirelessly across my windows network through my wireless router and onto my shared printer on my XP machine. It might be worth a shot??

---

### Post by jgordon510 on 2008-06-30
I tried the procedure at that link and still no luck.  

I'm pretty sure the problem is that the samba domain is outside of the wireless router's lan, and I'm trying to figure out how to print to the external domain.

---

### Post by superprash2003 on 2008-06-30
are you able to ping the windows machine(which has the printer) from the ubuntu laptop?

---

### Post by jgordon510 on 2008-06-30
Yes.  I can ping it.  But, I have limited admin privileges on the machine and I wasn't able to change the firewall settings.  I wasn't successful in opening the port. 
 
> **superprash2003 said:**
> are you able to ping the windows machine(which has the printer) from the ubuntu laptop?

---

### Post by superprash2003 on 2008-07-01
it could be some firewall blocking.. if possible try using the same ip you get when you are on a wired connection.. use that ip for the wifi connection(manually setup ip) and see if you are able to access printer..

---

