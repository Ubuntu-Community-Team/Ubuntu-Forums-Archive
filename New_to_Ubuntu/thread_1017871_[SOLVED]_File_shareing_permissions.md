---
title: "[SOLVED] File shareing permissions"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by lenelson on 2008-12-21
I need help with permissions for file services! Whenever I try to grant permissions fo a folder, I get the message: ...'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share. 
I can never get beyond this.
Lyle

---

### Post by drs305 on 2008-12-21
You are probably trying to share a folder owned by another user or by root. To enable sharing, you can do it via "gksudo nautilus" and then navigate to the folder, right click, Sharing Options, select the options you want to enable it. Whatever method you are trying to use, assume root privileges first.

---

