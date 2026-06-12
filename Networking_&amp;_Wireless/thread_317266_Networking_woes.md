---
title: "Networking woes"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by externalsupport on 2006-12-12
Hello all. 

I am having some network woes and I hope someone can help.

I have 3 webservers, 1 main server and 2 failover servers. The main server is hosted in our local office in the DMZ and is running Ubuntu 6.06 and running the usual LAMP configuration. The first fail over server is running Win 2000 (yet to switch to Linux as there are a few ASP pages that need converting). and the second failover server is in another office and is the same configuration as the local fail over server. The web folders on each of the windows servers are shared and I intend to use rsycn to keep them all synchronised. I am going to write a script that will mount the shared areas on each machine in turn and synchronise them with main server. This is all working apart from when I try to mount the shared area on the remote server I am getting the error[INDENT][COLOR=red]timeout connecting to 10.1.2.30:445
timeout connecting to 10.1.2.30:139
Error connecting to 10.1.2.30 (Operation already in progress)
4884: Connection to 10.1.2.30 failed
SMB connection failed[/COLOR]
[/INDENT]Mounting the shares on the two local servers is not a problem.

Here is my mounting command[INDENT][COLOR=red]sudo mount //10.1.2.30/websites /media/IM01/ -o username=*******,password=*******,dmask=777,fmask=777[/COLOR]
[/INDENT]Any help would be greatly received.

Stephen

---

