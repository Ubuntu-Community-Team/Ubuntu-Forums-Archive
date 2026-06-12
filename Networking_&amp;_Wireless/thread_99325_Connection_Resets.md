---
title: "Connection Resets"
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by atatistcheff on 2005-12-05
Ok, this is a pretty strange networking problem.  I'll try to describe the symptoms and hopefully it will ring a bell with somebody.  

I'm experiencing connection resets with SSH sessions, VNC, SAMBA sessions and it's also causing problems with web browsing using Firefox.  The symptoms vary depending on the application.

VNC - sometimes initial connections are refused. When I do connect the session disconnects after a few minutes of use regardless of whether it's idle or active.

SSH - similar to VNC.  Sometimes Putty says the connection is refused.  When the connection does work I will work for a while and then get a "connection reset by software" message disconnecting me from the host.

SAMBA - file share connections will disconnect from the MS Windows computers using them on the Ubuntu host.

Firefox - web browsing is intermittent.  It will work ok for a few pages and then the browser will take a long time to load a page, frequently timing out. 

Ok, here's the real kicker.  I'm running VMware workstation on this same Ubuntu machine (dual proc 6GB of RAM using the 686 dual proc kernel).  The TCP functions of the VM guest machines work flawlessly.  For example, a Windows XP VM also runs web browsing, email, MS Terminal services and I can connect to it all day with no problems whatsoever.  This sort of rules out the low level network connection issues like speed, duplex, etc.  It has to be something in the TCP stack itself that's causing this problem.  

Any ideas?  Anybody experienced this before?

Thanks!

---

### Post by atatistcheff on 2005-12-05
Ok - newbie mistake.  I had grabbed a static IP on a DHCP subnet "thinking" that any decent DHCP server would check to see if an IP was in use before giving it out.  Apparently, I was wrong.  This was simply an IP address conflict with some other machine.  

At least maybe it will help someone else if they run across this.

Later!

---

