---
title: "no secure webdav in hardy"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by ymp on 2008-04-28
under connect to server there is no longer a secure webdav option, and regular webdav will not allow me to access my organizations server

---

### Post by SpaceTeddy on 2008-04-30
mhm - yeah. That is definetly annoying. However, gnome-vfs still suports davs (i just tested it)...

open a filebrowser (your personal folder for example), and type in the address of your webdav as with davs in frot... 

> davs://myserver/path

that still works. I really don't know why they got rid of davs... rather annoying...

---

### Post by lazerradial2003 on 2008-08-02
Did this work for you? I can connect to none SSL webdavs but not SSL. I get: 

Error: HTTP Error: Connection terminated unexpectedly
Please select another viewer and try again.

The URL format I'm using is: davs://myurl.co.uk:2078

It also doesn't work without the port number, any suggestions anyone?

---

### Post by findus on 2008-08-14
Works perfectly for me - this has been driving me crazy as not being able to get to my work folders through Ubuntu has been a pain!  Thanks Space Teddy!

---

### Post by misterdasher on 2008-08-22
SpaceTeddy: Thanks for the recommendation.  I tried using variations of "davs://myserver/" in Nautilus, and one almost worked.  Perhaps if I tweaked and played around with it a bit more I might've found a solution.

For any future visitors to this thread: If you can't get Nautilus to work, you can use Konqueror.  That's what ended up working for me.  Though, acknowledged, it's not properly a solution, but only a work-around.

---

