---
title: "Trying to access a network drive"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by toasty_ghosty on 2007-09-11
Hello,
 I'm trying to access a windows network drive. I got Samba but I cannot seem to get it set up right. The drive doesn't have an IP address as it changes with each user. Any help?

---

### Post by obrient on 2007-09-11
Does the windows machine have a network name? For example my XP box is called media-cntr, which is DHCPd, and simple use that in the server field when I open connect to server. You might also be able to browse the network for the drive by going to **Places>Network Servers**. 

If that doesn't work you should be able to see the server by typing ```
smbtree
``` in the command line, **Don't enter a password** and then you should have a list of all of the Samba shares on the network. Just some thoughts.

---

### Post by toasty_ghosty on 2007-09-11
for some reason I'm just getting this:

 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
timeout connecting to 206.00.000.216:445
session request to SCOTT-PC failed (Not listening on called name)
session request to *SMBSERVER failed (Called name not present)

---

### Post by obrient on 2007-09-26
Hum sounds like the window machines sharing isn't set up correctly. You should take a look at the networking and sharing there, or see if you can see the window share another way. Not sure what that error means.

---

