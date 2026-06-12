---
title: "Execute commands via ftp or http"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by Shevilie on 2007-03-30
Well I got a server at home that I use a lot at work. The problem is that I sometimes mess with the sshd config - while using ssh and the reboot. Then sometimes I mess something up and need to travel home to reconfig it. Now if I had a backup of the main config.. Is there a way I could have it to copy the file and then reboot either by apache webserver or ftp (got dapper LAMP server).

---

### Post by stefan.ciobaca on 2007-03-30
Please describe in more details what you are trying to do.

---

### Post by Mr. C. on 2007-03-30
Create a second instance of sshd listening on another port (eg. 222), so that you have two sshd's running.  This way, if you mis-configure the main ssh server, you can always use the backup one to connect and resolve the problem.

 The second one will listen on the alternate port.  If you have a firewall, you will need to forward that port to your second SSH instance.

Be sure to get the config files correct - start by looking at the startup procedure in /etc/init.d/ssh.

MrC

---

