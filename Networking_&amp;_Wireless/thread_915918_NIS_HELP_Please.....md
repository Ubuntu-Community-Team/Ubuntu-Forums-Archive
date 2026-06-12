---
title: "NIS HELP Please...."
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by knichel on 2008-09-10
I am running 7.10 on a server and using NIS to deal with logins. *I use NFS to mount /home for users and DHCP for IP's. *Lately, for no aparent reason (at least that I can figure out), the students are logged in and suddenly they can do nothing and their workstations freeze and neet to be hard booted. *After the restart, they can not even log in. *I am guessing something is going on with NIS? *I tried to restart NIS on both the server and client and still nothing. *I end up restarting the sever and when it comes back up, dhcpd3-server will not start until I disable the internal interface and re-enable it. *After doing this, the students are able to log in and work again.

---

