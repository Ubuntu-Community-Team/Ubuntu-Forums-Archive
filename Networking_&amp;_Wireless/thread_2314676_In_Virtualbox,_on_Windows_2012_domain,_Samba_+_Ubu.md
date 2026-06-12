---
title: "In Virtualbox, on Windows 2012 domain, Samba + Ubuntu: Windows cant find share"
date: 2016-02-22
forum: Networking &amp; Wireless
---

### Post by ubn4 on 2016-02-22
In Virtualbox all machines have internal networking on a \16 netmask enabled. Have Windows 2012 set as my writable domain controller and my dns server for local name registration. I would like to setup a Samba Ubuntu server as my file server and I am pretty much done(Samba installed, added to domain, visible to all machines) but Window on all the domain clients/servers cannot see the shares available on the samba server. I can connect to the samba server through IP or its hostname, which is a good thing, when mapping a network drive in my windows 10 client or server 2012 DC and there are two network shares visible on my samba server, homes and a user directory. But when I try to go into the shares or create new folders in them, Windows gives an error saying that the server exists but Windows cant find a path to the share.


Any suggestions?





Help is appreciated.

---

### Post by christiaan3 on 2016-02-23
Maybe you can include a part of your samba configuration.
Know that capital letters are important when searching shares. "Test" and "test" are two different things.
You can try creating a very open share (no security) something like:
[B][testshare]
comment = Test Share
path = /srv/samba/testshare [/B](example)[B]
browsable = yes
guest ok = yes
read only = no
create mask = 777

[/B]Try if you can find and access the share this way.I hope this helped you in the first step solving your problem[B].

[/B]Christiaan

---

