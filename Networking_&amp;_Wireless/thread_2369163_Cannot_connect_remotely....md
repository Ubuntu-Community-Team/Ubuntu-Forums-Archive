---
title: "Cannot connect remotely..."
date: 2017-08-19
forum: Networking &amp; Wireless
---

### Post by aorick on 2017-08-19
I have been banging my head against this wall for days. I can connect to my Ubuntu server both by public ip and by dyndns from within my local network. I cannot connect from outside of my network by either method. I am able to access the internet from the server, I just cannot access the server from the internet. I know it is probably something simple that I am overlooking.

---

### Post by TheFu on 2017-08-19
Welcome to the forums.

Draw a diagram for the connectivity and label all the IPs, firewalls and ports involved.  Check that each is doing everything correctly.  There isn't any "automatic" method. It is all manual.

"cannot connect" is vague.  Which protocols?  By name or by IP?  What do the server and router logs show?  What do the client logs show?

Of course, you can't use non-routable protocols. ssh/sftp/scp are usually pretty easy to get working. Plain FTP is much harder because the ports change with each connection.  Samba is impossible to use over the internet without a VPN.  So ... which protocol(s) and ports?

---

### Post by aorick on 2017-08-19
I don't know what you're asking for lol. When I try to go to my self-hosted site, I can by going to XXX.duckdns.org or by using public.ip.address only while connected to my local network. If I try from anywhere else (by either method) I get a time-out error.

---

### Post by TheFu on 2017-08-19
What protocol? [https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)
Which port(s)?
What do the log files say?  [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

We cannot help without you helping us.

---

