---
title: "Samba share Western Digital external drive."
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by Mosato on 2008-10-15
Hey guys, this has been driving me nuts for the last couple of months so I guess its time for some collaboration solving now.

I own a 1TB WD external drive and getting ubuntu 8.04 server to work with it was fine-ish. Now getting it to play nice with samba is the real hurdle. The problem is that the permissions to the 1TB are fixed for some reason. Only 755 owner root, which causes some problems. Meaning a backup network drive is out of the question. A temporary fix is to give the samba share force user as root, but that is dangerous and I dont particularly like having it this way for long.

chmod verbos or chown tells me that it is indeed chaning the permissions, however tests and ls say otherwise.

What can I do to force (not chmod -f) but literally FORCE the WD or ubuntu to give up its current permissions and set them to what I need them to be?


Cheers guys! =D

---

### Post by Mosato on 2008-10-15
*bump* comeon guys, this is a security risk here. I would like some help asap.

---

