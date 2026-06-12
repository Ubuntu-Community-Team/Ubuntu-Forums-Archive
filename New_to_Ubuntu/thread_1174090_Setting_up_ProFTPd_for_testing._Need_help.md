---
title: "Setting up ProFTPd for testing. Need help"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by mvalviar on 2009-05-30
Hi, I've successfully installed LAMP but I'm having trouble setting up the ftp. Can anyone show me a configuration file that will enable an authenticated user full access to /var/www. I tried but I kept getting "Connection refused when I point my ftp client to localhost.

---

### Post by jonobr on 2009-06-03
Hello

You probably tried this already, but does FTP to the local host work?
That is, the machine you have LAMP on, if you ftp 127.0.0.1 or ftp localhost what does that say?

Cheers

---

### Post by superprash2003 on 2009-06-03
you probably have permission issues , install gproftpd , GUI for proftpd , will make your configuration a lot easier

---

