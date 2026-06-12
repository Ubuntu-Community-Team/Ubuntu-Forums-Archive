---
title: "xubuntu (samba) &gt; windows 7 shared hp deskjet 3940"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by mouseboyx on 2015-08-23
The windows 7 machine is set up with an hp deskjet 3940, with correct drivers, it is shared, with password protected sharing off, I can add the printer easily through system-config-printer the samba url is correct.

When I print anything from one of my two Ubuntu machines, the windows 7 machine receives it and puts it in the print queue the printer begins the normal warm up, and then the paper never feeds through the printer, and the document sits in the queue on the windows 7 machine until it is manually removed and the pc is restarted.

I tried installing a newer version of hplip from the official site [http://hplipopensource.com/](http://hplipopensource.com/) and configuring it with system-config-printer, and the same thing happened.

However printing from other windows 7 machines works.

Here is the printer section of my smb.conf:

```
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
```

---

### Post by mouseboyx on 2015-08-23
My current solution is to run windows xp in virtualbox, and send my requests that way, but it defeats the purpose.

---

