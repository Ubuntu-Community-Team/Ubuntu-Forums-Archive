---
title: "Internet Problems"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by nobull on 2008-07-15
I am running Ubuntu 6.06 LTS as a file server and recently I changed some hardware around and can not connect to the internet for updates.  I have checked my network interfaces and my resolv.conf file but everything seems to look ok.  Any ideas?

---

### Post by superprash2003 on 2008-07-15
your getting an ip when you type ifconfig?? also try pinging a website and post output

---

### Post by nobull on 2008-07-15
Yes I am getting an ip address when I type ifconfig and it will show up on my LAN(Samba and NFS) but it will not resolve a host name when I ping or try to update(Apt-get or aptitude).  BTW, thanks for the prompt reply.

---

### Post by Loukisgr on 2008-07-15
tell us something. try nslookup [www.google.com](www.google.com) Any luck?

---

### Post by Iowan on 2008-07-15
What hardware did you change - the modem, router, or other internet access device?

---

### Post by nobull on 2008-07-19
nslookup returns "connection timed out.  No server could be reached."  I was at a temporary location and I was just using it as file server with a client.  The client was using wireless for the internet and the wired for the LAN connection to the server.  The server itself did not have an internet connection.  Now I have it directly hard-wired into a router with a static ip.

---

