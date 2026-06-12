---
title: "Problem with Ubuntu to view my samba server"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by cloudlor on 2008-09-29
My ubuntu can't show the samba server in the Network GUI. But can use the command to connect the problem. Anybody face this problem before?

---

### Post by jerome1232 on 2008-09-29
Yeah that's a (imho) major known bug in gnome, it can't browse authenticated shares, a workaround is to pop open nautilus, then hit ctrl+l
and type 

'smb://hostname/sharename' If you want easier access just bookmark it, hit ctrl+d and it should now appear in your places menu

so if I want to browse my computer 'joe' and access the share Public

smb://joe/Public will get me there

---

### Post by cloudlor on 2008-09-29
oh, thank you for helping.

---

