---
title: "HOW TO: configure fileserver"
date: 2005-09-20
forum: Networking &amp; Wireless
---

### Post by tram200050 on 2005-09-20
i have install UBUNTU and i think it is good to replace my old filesever into this, but the problem is i am new to it, can somebody help and guide me to configure this UBUNTU into fileserver.

i have already install the desktop, now whats next to configure FILESERVER.

thanks in advance.

---

### Post by KingBahamut on 2005-09-20
That depends on entirely which type of envoirnment your going to function in. 

If totally unix based - NFS. 
If totally windows based - Samba 

Alternate method could be something like LDAP. 

The real question is, what are the clients who are accessing that information across the network running for their machines? Windows? Linux? Unix? Mac?

---

### Post by tram200050 on 2005-09-21
big thanks for the reply.

the server that i would like to create will be accessed by windows.

---

### Post by KingBahamut on 2005-09-21
[QUOTE=tram200050]big thanks for the reply.

the server that i would like to create will be accessed by windows.[/QUOTE]
 apt-get install samba samba-common 

Then share your directories out. Youll probably need to replicate login data from the other machines on the network for authentication purpose (Primarily because I wouldnt advise anon access to any samba share on your network , just as I would never allow Everyone Access to a windows share on a windows network, call me paranoid, its ok, happens all the time). 

That be said, do that, then place your data, and have fun. 

Might not hurt to install clamav either, if for no other reason to keep data clean of viral contagion.

---

