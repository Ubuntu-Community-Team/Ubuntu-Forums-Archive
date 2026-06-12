---
title: "Can't ping netbios name of winxp on local network"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by DePurpereWolf on 2010-10-31
I'm trying to set up a local network between my ubuntu pc and windows xp pc.
I've installed samba, and followed many tutorials and howto's to get it running. 
I believe that something elementary isn't working properly.

I can ping the other pc with the ip address, but not with the netbios name.
Which I should be able to do right? 
The samba howto states that if this happens my TCP/IP software isn't correctly installed, but I have no idea on how to fix that. 

Also the swat page says that smbd and winbindd is running, but nmbd isn't. When I try to start the service from the command line it says that it's already running.

Does anyone have any pointers for me on where to start looking. Most information about Samba I can find doesn't provide much troubleshooting info about this particular problem.

---

### Post by spiky001 on 2010-10-31
Ok you have to add pc name to /etc/hosts  eg ip    pcname

---

### Post by DePurpereWolf on 2010-11-01
Yes, that fixed that part. I can ping by net bios name now.
Thanks for the help.

---

