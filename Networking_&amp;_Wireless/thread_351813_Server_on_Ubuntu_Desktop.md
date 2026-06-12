---
title: "Server on Ubuntu Desktop?"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by mrpeenut24 on 2007-02-02
Is it possible for me to set up a server on Ubuntu Desktop 6.10?  I don't need this as a dedicated server, in fact, this is meant to be a desktop with serving capabilities.  Basically I just need to be able to connect to myself to test out some CGI script projects and perhaps a few websites, not so much for hosting.  Although I might need the works (LAMP-like).   I might also like to connect from another computer in my LAN but nothing large-scale enough to need the server as the base.

Thanks.

---

### Post by kpatz on 2007-02-02
Yes, you can use apt-get, aptitude or Synaptic to install the server packages onto your desktop install.  You'll want to get Apache 2, PHP 5, MySQL 5 for a LAMP type configuration.  You'll probably also want Samba (to share/connect to Windoze boxes), OpenSSH (to log in remotely), maybe an FTP server, NFS, etc.

---

### Post by Floppyjoe on 2007-02-02
> **mrpeenut24 said:**
> Is it possible for me to set up a server on Ubuntu Desktop 6.10?  I don't need this as a dedicated server, in fact, this is meant to be a desktop with serving capabilities.  Basically I just need to be able to connect to myself to test out some CGI script projects and perhaps a few websites, not so much for hosting.  Although I might need the works (LAMP-like).   I might also like to connect from another computer in my LAN but nothing large-scale enough to need the server as the base.

Thanks.
there are instructions for setting up a lamp server at this url:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by mrpeenut24 on 2007-02-03
Thanks!  That was just what I needed. :-)

---

