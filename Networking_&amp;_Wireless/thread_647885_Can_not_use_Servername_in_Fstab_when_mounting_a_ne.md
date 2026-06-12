---
title: "Can not use Servername in Fstab when mounting a network folder?"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by Tsi99 on 2007-12-22
I am able to mount the network folder with fstab using the ip address for the server.  The problem is I am on a network with DHCP.  The server is usually one of four ip addresses.

I am using cifs for the file system tag.  Also, the server name doesn't have any spaces in it.

Any ideas on getting fstab to work with the server name?

Thanks,
Matt

---

### Post by Tsi99 on 2008-01-04
Solved
installed winbind package
and added wins to host in nsswitch.conf 

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/31975c390f59ffeb/375527e841dacb44?lnk=raot](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/31975c390f59ffeb/375527e841dacb44?lnk=raot)

---

