---
title: "proftpd won't run"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by vdhagen on 2006-12-30
Hi,
I have to access my ubuntu-backup-pc from Windows ME. (For W2K I  solved all problems: map network drive as ubuntu-user who owns the mounted raid5 array.)

Probably the easiest way is FTP, right? (I intend using something like FTPsync.)  All takes place in a local network to which a router (192.168.1.1) provides local (static) IP addresses. The ubuntu-pc has ip address 192.168.1.4.

However, I can't get it to work. Starting the proftpd as servertype "inetd" I get the message "ProFTPd is started from inetd" but "ftp 192.168.1.4" leads to "connection refused".

Starting with servertype "standalone" I get the strange messages:
 - IPv4 getaddrinfo '192.168.1.1.168.1.1' error: Name or service not known
 - warning: unable to determine IP address of '192.168.1.1.168.1.1'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'

I have no idea where the systems gobbles up that address. Any helpful comments?

Oskar von dem Hagen

---

### Post by kptracey on 2007-03-21
I have the same problem and I have found no reply on the forums.

Were you ever able to resolve?

---

