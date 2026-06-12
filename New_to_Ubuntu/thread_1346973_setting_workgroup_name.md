---
title: "setting workgroup name"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-05
Hello


Need computer on home network be configured for the same workgroup name.I know how
to this in vista but not in Ubuntu.The purpose for this is:Printer Sharing.Printer to be shared
is connected to pc running windows vista home premium.THANKS in advance.Both desktops and laptop connected to router to share internet connection.

---

### Post by bab1 on 2009-12-06
> **manny43 said:**
> Hello


Need computer on home network be configured for the same workgroup name.I know how
to this in vista but not in Ubuntu.The purpose for this is:Printer Sharing.Printer to be shared
is connected to pc running windows vista home premium.THANKS in advance.Both desktops and laptop connected to router to share internet connection.

You can set the WORKGROUP directive in the /etc/samba/smb.conf file.  It's near the top in the "Global" section.

---

