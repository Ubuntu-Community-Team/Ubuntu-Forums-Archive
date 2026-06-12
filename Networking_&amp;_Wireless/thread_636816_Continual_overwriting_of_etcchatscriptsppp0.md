---
title: "Continual overwriting of /etc/chatscripts/ppp0"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by CorporateGoth on 2007-12-10
OK, I can't find this anywhere.

I am having a problem where the file /etc/chatscripts/ppp0 keeps getting overwritten every time I change network locations (and possibly more frequently).  This would not bother me so much, but somewhere along the way, I had a typo in my /etc/chatscripts/ppp0 file and THAT file was saved somehow and keeps overwriting the CORRECT file every time I try and switch network profiles to use the ppp0 (which happens to be an EV-DO) connection.

This means every time I want to use my BroadbandAccess, I am forced to switch profiles, then sudo vi /etc/chatscripts/ppp0 and remove the typo - this is getting to be highly annoying, and I cannot for the life of me figure out which process keeps 'helpfully' overwriting this file for me.  I think it is something to do with NetworkManager, but an strace showed it not to be touching that file, but I don't believe NetworkManager does much work directly anyway.

In any case, I need help to stop this file getting overwritten before I decide to say screw it and use a distribution that will only touch files when I tell it to :(

PreZ

---

