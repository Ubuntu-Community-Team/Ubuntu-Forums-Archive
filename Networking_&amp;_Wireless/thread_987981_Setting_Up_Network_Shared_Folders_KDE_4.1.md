---
title: "Setting Up Network Shared Folders KDE 4.1"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by Redlazer on 2008-11-20
I'm having some issues sharing folders with KDE 4.1.

When I right click on a folder, and click on the sharing tab, nothing happens. 

Anyone have any experience with this issue, and can point me towards a solution?

Thanks in advance!

-Fred

---

### Post by superprash2003 on 2008-11-20
are you trying to share folders using samba?

---

### Post by Redlazer on 2008-11-20
Yes.

---

### Post by superprash2003 on 2008-11-21
post output of smb.conf file .. go to places->COmputer and under Go To type smb://127.0.0.1 .. do you see your shared folders?

---

### Post by Redlazer on 2008-11-23
Ok, I'm onto something. 

It seems to me just a bug in KDE4.1 preventing the call from going through. I never see any wizard or anything.

However, that's juuuust fine. I'm aiming more for a command-line solution anyways, as I'm trying to teach myself remote administration.

So, where in the smb.conf file (presumably?) and with what syntax do I manually add shared folders?

-Fred

---

### Post by superprash2003 on 2008-11-24
/etc/samba/smb.conf .. command line solution [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html) step 9

---

