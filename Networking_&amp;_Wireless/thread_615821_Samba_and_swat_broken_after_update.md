---
title: "Samba and swat broken after update"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by rolen on 2007-11-17
Hi, 

Looks like the Samba( am on 7.10) update the other day has broken my samba and swat(windows saying that the share no longer exists). Share appears in System->Admin-> Shared Folders.  It looks like my smb.conf was preserved although the file time was touched so not sure if it was changed. The daemon seems to start up okay, nothing in the smbd.log or nmbd.log.  Have done a smbpasswd.

Has anyone come across this and fixed it? Your help would be greatly appreciated.

Find it ironic that an update desgined to stop a potential DoS has busted my system when it was working perfectly...

Rob

---

### Post by HermanAB on 2007-11-17
There is a new Samba version coming out on Monday.  See samba.org for details.

---

