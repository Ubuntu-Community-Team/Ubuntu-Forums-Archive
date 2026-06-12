---
title: "Samba,Ubuntu Speed Issues"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by thavinci on 2008-06-11
Please Help!!!! I have a file server i recently converted to ubuntu.
Since then it's only been issues.

Seems with file sharing it would copy full speed and then "get stuck" , no comms to files on server anymore. (From any pc on network)

After a little while all continues till next glitch...

Any help/advise?

---

### Post by dmizer on 2008-06-12
start by posting your /etc/samba/smb.conf file.  what about firewalls?

---

### Post by thavinci on 2008-06-12
Was no firewalls at all.

Was default config only added shares within webmin.

No other changes what-so-ever.

Had to since change back to FreeBSD, stable as a rock.

Thank you for offering to help though!

---

### Post by dmizer on 2008-06-12
just for future information, the default smb.conf needs to be changed in order to properly handle file sharing.

---

