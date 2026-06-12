---
title: "Bind on a workstation?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by dave66 on 2009-05-13
Hi,

I was hoping somebody could help me. I'm setting up some netbooks for use by field staff. They will not be networked and will only occasionally sent data via FTP/SFTP to a central server. Applications such as Firefox/Email will not be installed or used. 

So I'm wondering, do I need to have bind9-host installed at all, from what I can gather it is only used if Ubuntu is being used as a server. I'm trying to lock down the units as much as possible and either remove or disable apps/services which are not required.

Any help would be appreciated.

---

### Post by bswilson on 2009-05-13
Great question.  The bind9-host package gives you the host utility to look up hosts (e.g. resolve names).  I would think that if you only have an occasional need to SFTP/FTP to some systems, you could put those addresses in an /etc/hosts file or something.  However, I'm not sure if you'll get an /etc/resolv.conf file if you don't install some bind components...

---

