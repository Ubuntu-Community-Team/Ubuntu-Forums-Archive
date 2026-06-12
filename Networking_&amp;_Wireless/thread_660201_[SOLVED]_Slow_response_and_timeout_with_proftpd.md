---
title: "[SOLVED] Slow response and timeout with proftpd"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by trygveaa on 2008-01-06
I have a server with ubuntu, and run proftpd on it. When I log on to the ftp-server and browse the folders it sometimes takes very long time to open the folder, and if I use SmartFTP I get the message "Server closed connection". This happens every second or third time I open a folder. The rest of the times, the folder opens at once. This happens in all folders.

To access the ftp-server I have tried Konqueror, Nautilus, Windows Explorer, SmartFTP and Opera. I don't have this problem with Opera or Konqueror, but with the three other programs.

I have added this in proftpd.conf, because many persons say it makes the ftp-server faster:
IdentLookups off
UseReverseDNS off


When I connect to ssh, the server is slow if I use the local IP, but if I use the external IP it responses at once. Before I deactivated ipv6, ssh was slow with the external IP also. I don't know if this has a connection to proftpd, but maybe it's possible. I didn't notice any difference in proftpd with ipv6 off or on.

I deactivated ipv6 with adding this to /etc/modprobe.d/aliases:
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off


I will attach the proftpd.conf file, but I don't think it is something wrong in it, because it is mostly the same as a friend of mines, and he don't have this problem. SSH is also fast at his server, even though he hasn't deactivated ipv6.

---

### Post by trygveaa on 2008-02-11
I have now tried with vsftpd instead of proftpd, and have exactly the same problem. Doesn't anyone have any idea what could be wrong?

---

### Post by trygveaa on 2008-02-13
I have finally solved my problem. It had nothing to do with proftpd or ubuntu at all. My router D-Link DIR-655 had a firewall with some trouble with ftp. I found my answer [here]("http://www.dslreports.com/forum/r19056356-FTP-Active-not-working-going-through-DIR655") in the second last post:

Log in to the router, click advanced and then Firewall settings. Disable the SPI and change the NAT ENDPOINT FILTERING to endpoint independent.

---

