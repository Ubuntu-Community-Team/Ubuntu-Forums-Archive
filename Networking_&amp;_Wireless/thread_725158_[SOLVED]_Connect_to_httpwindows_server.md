---
title: "[SOLVED] Connect to http://windows_server"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by rolodoom on 2008-03-15
Hello. Well, we use my Linux as server for our LAN.  Last week we change the server to a windows machine. The problem: My Linux connect to windows server only (and repeat **ONLY**) using IP address: [COLOR=Red]http://10.1.1.3[/COLOR], I have test it using nautilus ([COLOR=Red]smb://10.1.1.3[/COLOR]) and Firefox and both have the same result.

Linux cannot connect using the server name (in this case [COLOR=Red]http://servername[/COLOR]) as the windows machines.

Repeat, Linux, can not connect neither using [COLOR=Red]smb://servername[/COLOR] nor [COLOR=Red]http://servername[/COLOR] but IT **DOES** connect using IP address instead of the name.

I don't really know how to fix this but think that I'm missing a little trick somewhere.

Thanks.

---

### Post by Iowan on 2008-03-15
One option would be to edit your /etc/hosts file.

---

### Post by rolodoom on 2008-03-17
Thanks. Problem solved.

---

