---
title: "Trouble Connecting to School's WPA-TKIP network"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by psynaptic on 2008-04-04
Hi everyone. I'm a complete nubnub as this is my first linux install. I'm running on a Sony VAIO vgn-s360p and on Gutsy. I can connect to my home WPA2 network with wicd and troubleshooted it with the informative posts here. However my luck ends when trying to connect to my school's network. I have connected to the school's network on the same laptop in windows without a problem (it asks for my student number and password to login). The configuration instructions for windows are here.

[WIndows Wireless Instructions](http://anonym.to/?"http://its.dc-uoit.ca/mobile/pdf/Wireless%20Configuration.pdf")


I have tried to follow the posts here but it has not worked. 
[http://ubuntuforums.org/showthread.php?t=662379]("http://ubuntuforums.org/showthread.php?t=662379")

Since I am using wicd, what should I do to connect? I have removed the bit on CA_cert in the templates to no avail.

Thanks in advance.

---

### Post by spd106 on 2008-04-06
The link you've posted to just points to a script held on an intranet (local) server. You're probably going to need to to open the runme.bat file with a text editor and see what it uses for it's settings and whether it installs a certificate that you will need in order to authenticate with the server.

---

