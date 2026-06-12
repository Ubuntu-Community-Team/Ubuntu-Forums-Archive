---
title: "Accessing windows shares from VMWare install"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by seeker1458 on 2008-06-09
I have installed Hardy via VMWare server.  I can see all the machines in my domain (used likewise open) but when I open machines in Nautilus they are just empty.  The shares I am trying to access are setup for _Everyone_ to have read/write/modify permissions, so I know its not a security setting.  What do I need to check...samba,winbind,kerberos?  Anythoughts??

---

### Post by superprash2003 on 2008-06-09
are you able to access by typing smb://(ip of share)

---

### Post by seeker1458 on 2008-06-10
No, it just opens an empty window.

---

### Post by superprash2003 on 2008-06-10
empty window?are you sure you have shared the folders properly?able to see it from another pc? are you able to ping the ubuntu machine from windows?

---

### Post by seeker1458 on 2008-06-13
Yes, every other machine on the domain can access these shares.  Yes I can ping the Hardy box, it even registered itself with Active Directory when joining via likewise.   Sorry for the delayed response...things have gotten crazy busy here and I haven't had time to play.

Edit: as a matter of fact...I am writing this while using TightVNC to VNC into the ubuntu box.

---

