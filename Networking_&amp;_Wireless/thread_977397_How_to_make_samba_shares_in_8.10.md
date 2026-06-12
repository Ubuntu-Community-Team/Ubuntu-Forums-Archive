---
title: "How to make samba shares in 8.10 ?"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by yesint on 2008-11-10
Dear All,
I'm trying to configure samba in Interpid. I installed samba and it works correctly (network printers work and I see other Windows machines), however I can't figure out how to make my computer visible and share the folders. My computer is not seen in the network and I can't understand where to set the name of windows workgroup. Any suggestions?

---

### Post by AlanR8 on 2008-11-10
Had similar issues in Kubuntu 8.1.

You'll have to edit the file /etc/samba/smb.conf

Find the line that says workgroup = workgroup and change the name to your Windows workgroup. Reboot and all should be well.

I also installed system-config-samba that provides a graphical interface for creating new shares and applying samba permissions.

---

### Post by yesint on 2008-11-10
Many thanks! I'll try.

---

