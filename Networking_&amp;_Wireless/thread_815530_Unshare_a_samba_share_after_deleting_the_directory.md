---
title: "Unshare a samba share after deleting the directory"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by mishkind on 2008-06-01
Hi,
I set up some samba shares by right clicking the folders and setting the sharing options.
This was a long time ago, and since then I deleted the folders that I was sharing.
The problem is that when I view my network, it still lists all the folders that I had previously shared, except of course if you try to go into the folder it gives an error.
Is there a way to remove these old, non-existent shares?
thanks,
mishkin

(ps. running hardy)

---

### Post by Prospero2006 on 2008-06-01
The master configuration file is located in

/etc/samba/smb.conf

Down at the bottom of those files you should see the shares set up.
Delete the entries

---

