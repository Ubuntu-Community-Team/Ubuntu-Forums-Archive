---
title: "Ubuntu on windows server"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by doonites on 2007-10-05
Is there any way or softwarfe by which i can connect ubuntu7.04 client onto my windows server 2003, so that it can act as member of servers, and the users in actice directory can access ubuntu!!!!!

---

### Post by El Rogueo on 2007-10-05
try samba, which may or may not come with the distro


some light reading~
[http://en.wikipedia.org/wiki/Samba_(software](http://en.wikipedia.org/wiki/Samba_(software))
[http://handsonhowto.com/smb101.html](http://handsonhowto.com/smb101.html)

as always, google is your friend

---

### Post by doonites on 2007-10-05
i have tried sanba but still no success, i can join the ubuntu and windows server without creating any mess its easy, but the problem is that my ADS and policies are not affecting ubuntu, nor my ads client can open their accounts in ubuntu.....

---

### Post by El Rogueo on 2007-10-05
wow. samba's really as far as I go there if you can't get that to work.

do you get any messages when you can't get the clients to open their accounts? or is it just not possible

Sorry I can't help you more, but if you can connect but the policies don't work I really dunno.

good luck

---

### Post by doonites on 2007-10-08
ya it gives an error like " user does not exist", but in my ads the user exist.

---

### Post by El Rogueo on 2007-10-08
That's pretty weird....

yeah I'm sorry I can't be of more help, hope something works out and gl

---

### Post by helgman on 2007-10-08
You need to make sure that the Ubuntu Server uses AD for authentication. There should be a HOWTO out there somewhere. Search for it. SAMBA is the right (only?) way to do it.

As for policies you might get a hard time making most of em work since they are made for Windows machines and the wonderful Windows Registry. Linux don't use that ...

Regards,
Helgman

---

