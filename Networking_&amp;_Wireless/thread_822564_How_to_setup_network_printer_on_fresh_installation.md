---
title: "How to setup network printer on fresh installations?"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by asdir on 2008-06-08
Can anyone tell me how to set up two Ubuntu-boxes, so that I can print from one using the printer of the other via network?
One PC has Gutsy and an installed printer, the other has Hardy installed.

Is there any easy Point-and-Click method for this? Trying to check and uncheck boxes in the printer and network setup did not work for me.

Pointing me to tutorials or howtos is okay, too.

---

### Post by superprash2003 on 2008-06-08
one way to do this is via samba [http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html)
set up the gutsy pc as shown and in the hardy pc go to system->administration->printing ..then click on NEW PRINTER and select WINDOWS PRINTER VIA SAMBA and enter ip address of gutsy pc with username/password etc..

---

### Post by asdir on 2008-06-08
Isn't there a native linux variant (I mean, with NFS instead of Samba)? Or would that be too complicated?

Anyway: Thanks.

---

